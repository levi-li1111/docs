# 几种不同类型的IO
- BIO  NIO  AIO
### 阻塞 VS 非阻塞 
- 主要看方法是否实时返回 还是卡在那里不动等着 while 尝试读取
### 同步 VS 异步 主要看是当前线程中 处理 还是 通过回调函数处理（可能当前线程 也有可能重新起线程）