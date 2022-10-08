## 主从复制模式
### 同步模式 
- 异步同步模式
- 半同步模式 -- 解决主从数据的一致性的问题，但又是时间会比较长
- GTID同步模式
### Redo Log -- InnoDB 引擎特有的日志 -- 提供crash-safe 的能力 物理日志 循环写 prepare commit 两阶段提交
- Server 层 + 存储层
### bin log -- server 层 逻辑日志 -- 追加写

### mysql 运维语句总结
- 事务查询语句
select * from information_schema.innodb_trx where TIME_TO_SEC(timediff(now(),trx_started))>60;
- 查询事务隔离级别: show variables like 'transaction_isolation';
- MVCC 多版本控制 -- 一把尺子量出你能看到的版本 
    - 隐藏列: row_id， trx_id 自增,  roll_PTR 地址  保底
    - 链表结构 保存多版本
    - 快照读 select
-   - 大于cur_trx_id 一定不能看到
    - = cur_trx_id 肯定看到
    - < cur_trx_id 提交可以看到 未提交看不到
    - active 和之前的一个 
    - m_ids readviews 
    - begin -create readview 通过readview 去量 快照读 readview 在创建之后不会再改变
    - 当前读 - select .. for update, delete, update, insert readview 重构
- INNODB B+Tree 索引数据结构
- 覆盖索引避免回标 考虑冗余联合索引情况 
- 前缀索引、 最左匹配原则 最左前缀可以是联合索引的最左N个字段，也可以是字符串索引的最左M个字符。
- 索引下推  索引上有需要的值 先比较 再回表
-  alter table T engine=InnoDB 重建主键索引方案
- mysql 锁
    - 全局锁 -- 全库逻辑备份
    - 表级锁  
        - lock tables
        - MDL (metadata lock)  增删改查都会先申请MDL读锁
    - 行锁 - 引擎级别
        -  两阶段锁协议： 在InnoDB事务中，行锁是在需要的时候才加上的，但并不是不需要了就立刻释放，而是要等到事务结束时才释放。这个就是两阶段锁协
    - innodb_lock_wait_timeout 死锁与死锁检测 锁等待时间
    - innodb_deadlock_detect on -- 开启死锁检测 主动回滚死锁链条中的某一个事务
按照效率排序的话，count(字段)< count(主键id)< count(1)≈ count(*)
- Update 为当前读
- select 语句如果加锁，也是当前读
- 读锁（S锁 共享锁） 
- 写锁 (X锁，排他锁)
