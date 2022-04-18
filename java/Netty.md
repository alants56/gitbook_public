# Netty



## 1.Netty是什么

Netty是一个异步的、基于时间驱动的网络应用框架，用于快速开发可维护、高性能的网络服务器与客户端。



## 2. Demo

**依赖**

```
<dependency>
  <groupId>io.netty</groupId>
  <artifactId>netty-all</artifactId>
  <version>4.1.52.Final</version>
</dependency>
```



**服务器**

```java
public class HelloServer {
    public static void main(String[] args) {
        new ServerBootstrap()
                .group(new NioEventLoopGroup())
          			// boss和worker，boss负责ServerSocketChannel上的accept，worker负责读写
                .group(new NioEventLoopGroup(),new NioEventLoopGroup())
                .childHandler(new ChannelInitializer<NioSocketChannel>() {
                    @Override
                    protected void initChannel(NioSocketChannel nioSocketChannel) throws Exception {
                        nioSocketChannel.pipeline()
                                .addLast(new StringDecoder())
                                .addLast(new ChannelInboundHandlerAdapter(){
                                    @Override
                                    public void channelRead(ChannelHandlerContext ctx,Object msg) throws Exception {
                                        System.out.println(msg);
                                    }
                                });
                    }
                })
                .bind(8765);
    }
}

```



**客户端**

```java
public class HelloClient {
    public static void main(String[] args) throws InterruptedException {
        new Bootstrap()
                .group(new NioEventLoopGroup())
                .channel(NioSocketChannel.class)
                .handler(new ChannelInitializer<NioSocketChannel>() {
                    @Override
                    protected void initChannel(NioSocketChannel nioSocketChannel) throws Exception {
                        nioSocketChannel.pipeline()
                                .addLast(new StringEncoder());
                    }
                })
                .connect(new InetSocketAddress("localhost",8765))
                .sync() //阻塞，直至建立连接
                .channel()
                .writeAndFlush("Hello Netty!");
    }
}
```



## 3. EventLoop

### 1.**EventLoop**

EventLoop单线程执行器，run方法处理Channel上的io事件



### 2.**EventLoopGroup**

一组EventLoop，Channel会调用EventLoopGrop的register方法来绑定一个EventLoop，后续io就由此EventLoop来处理。



### 3.EventLoop创建

NioEventLoopGroup

io事件，普通任务

```java
EventLoopGroup group = new NioEventLoopGroup(2);
group.next().submit(()->{
	System.out.print("HAHA")
})
```

定时任务

```java
EventLoopGroup group = new NioEventLoopGroup(2);
group.next().scheduleAtFixedRate(()->{
  System.out.print("HAHA")
},1,1,TimeUnit.SECONDS)
```



DefaultEventLoopGroup

普通任务，定时任务



### 4.Channel

* close()
* closeFuture() 
    * sync
    * addListener
* pipeline() 添加处理器
* write()
* writeAndFlush()



ChannelFuture获取channel

```java
channelFuture.sync()
Channel channel = channelFuture.channel()
```



```java
channelFuture.addListener(new ChannelFutureListener(){
	@Override
	public void operationComplete(ChannelFuture future) throws Exception {
	
	}
})
```



### 5.Pipline

1. ChannelInboundHandlerAdapter

​	入栈执行

2. ChannelOutboundHandlerAdapter

​	出栈执行

* channel.writeAndFlush() 从tail向前找

* ctx.writeAndFlush() 从当前向前找



### 6. ByteBuf

1.创建

```
ByteBuf buf = ByteBufAllocator.DEFAULT.buffer(10)
```

```java
//调试
public static void log(ByteBuf buff){
  int length = buff.readableBytes();
  int rows = length/16 + (length%15 == 0 ? 0 : 1) + 4;
  StringBUilder buf = new StringBuilder(rows*80*2)
    .append("read index:").append(buff.readerIndex())
    .append(" write index:").append(buff.writeIndex())
		.append(" capacity:").append(buff.capacity())
    .append(NEWLINE);
  appendPrettyHexDump(buf,buff);
  System.out.println(buf.toString());
}
```



2. 直接创建和堆内存

```
ByteBuf buf  = ByteBufAllocator.DEFAULT.heapBuffer(10)

ByteBuf buf  = ByteBufAllocator.DEFAULT.directBuffer(10) //默认
```



3. 池化

> 可以重用ByteBuf，高并发时，池化能更节约内存，减少内存溢出的可能



4.组成

* 容量
* 最大容量
* 读写指针

5.写入

* writeBoolean()
* writeBytes()
* ... ...

6.读取

```
buffer.readByte()
buffer.marReaderIndex()
buffer.resetReaderIndex()
```

7.释放

ReferenceCounted

* release
* retain

8.零拷贝

* slice 切片

* composite



