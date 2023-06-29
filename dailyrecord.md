####    6月21日
*   完成相关的软件安装 和 环境配置
*   测试开发环境
*   5G知识学习

*   5G
    *   BaseLine
        *   技术 
        *   新场景         

*   无线网络基础
    *   信源 => 发送器 => 信道（传输会衰减，信道有噪声和干扰） => 接收器 => 信宿
    *   通信流程 ： 电路交换 + 分组交换
    *   复用和多址
        *   复用：一条信道同时传输多路数据
        *   多址：一条信道同时传输多个用户数据

####    NR软件架构
*   DOPRA   开放的面向对象的分布式可编程实时框架
    *   软件开发和运行控制
*   HERT华为增强无线技术
*   实时视图
    *   FID / PID编程框架
    *   FID function idetification
        *   下面有多个PID
        *   串行进行 + 共用消息处理队列和消息队列
*   

####    6月25日
*   [完成SSH公钥配置](https://codehub-y.huawei.com/profile/keys)
*   找曾圆老师添加权限，以供在资源管理器访问自己的目录
#####   ExpertProduct(问题定位故障树)
######  代码结构
*   tree web源码
    *   dir_x  => 一个节点
    *   file.py 记录该节点的内容
    *   dir_x_1/2/3  子节点
*   core 接口
    *   lib.py 数据解析接口 
    *   lang.py 内置接口
*   data 中间生成数据
*   standard_format.py 规范化操作

######  编写故障树步骤
*   找父节点 => 创建子目录和子文件，编写问题案例代码 => 验证(根据是否有区别) => 上库
*   主要要求是：结构化操作 + 业务
######  使用故障树步骤 
*   选根节点 => 开始运行，输入数据 => 结果


####    6月26日
*   [安装idea + JDK 8](https://developers.redhat.com/products/openjdk/getting-started?success=true&tcWhenSigned=January+1%2C+1970&tcWhenEnds=January+1%2C+1970&tcEndsIn=0&tcDuration=365&tcDownloadFileName=java-1.8.0-openjdk-1.8.0.372-1.b07.redhat.windows.x86_64.zip&tcRedirect=5000&tcSrcLink=https%3A%2F%2Fdevelopers.redhat.com%2Fcontent-gateway%2Fcontent%2Forigin%2Ffiles%2Fsha256%2Fcf%2Fcf846456fb61e52b3c96fd4a4d132cc59abff2b4ee4bdc4fe9f9000b098707ad%2Fjava-1.8.0-openjdk-1.8.0.372-1.b07.redhat.windows.x86_64.zip&p=Product%3A+OpenJDK&pv=April+2023&tcDownloadURL=https%3A%2F%2Faccess.cdn.redhat.com%2Fcontent%2Forigin%2Ffiles%2Fsha256%2Fcf%2Fcf846456fb61e52b3c96fd4a4d132cc59abff2b4ee4bdc4fe9f9000b098707ad%2Fjava-1.8.0-openjdk-1.8.0.372-1.b07.redhat.windows.x86_64.zip%3F_auth_%3D1687767609_e936be621e8050ea1da5f11dc388b39c)
*   Java IO系列复习

### 6月27日
*   遇到的问题:  Failed to retrieve plugin descriptor for org.apache.maven.plugins:maven-compiler-plugin:3.1: Plugin org.apache.maven.plugins:maven-compiler-plugin:3.1 or one of its dependencies could not be resolved: Failed to read artifact descriptor for org.apache.maven.plugins:maven-compiler-plugin:jar:3.1
    *   

#    Java 学习
##   基本介绍
*   Netty : 基于NIO的客户端/服务器编程框架
    *   优势
        *   API使用简单
        *   功能强大

*   Redis : 远程字典服务器
    *   纯内存数据库，数据存取速度很快
    *   应用场景
        *   缓存
        *   分布式会话
        *   任务队列
    *   成为缓存事实标准的原因
        *   速度快
        *   丰富的数据结构
        *   单线程
        *   可持久化
*   ZooKeeper
    *   分布式协调工具
    *   优势
        *   实现了分布式环境数据一致性
        *   类似于简单的分布式数据库
            *   区分各类读
                *   脏读 ： 一个业务访问到了另外一个业务没有提交的数据
                *   不可重复读 ： 一个事务对数据进行多次查询，但是结果却完全不一致
                *   幻读 ： 是指当两个完全相同的查询执行时，第二次查询所返回的结果集和第一次查询所返回的结果集不相同
                *   幻读关注的是新增或者删除，不可重复读关注的是记录的更新
    *   高性能HTTP通信技术
        *   QPS在十万级甚至千万级以上
        *   架构层可以分为：服务层、接入层和客户端层
        *   NiginX 处理高并发的HTTP请求
    *   微服务RPC
    *   高并发IM 即时通信

##  外传
### lombok

### JDK
*   目前在内网可以涉及访问的JDK包括red hat的JDK还有oracle的
*   但同时如果需要使用内部主流的框架的话需要使用Huawei-JDK
    *   和redhat的JDK其实是类似的
    *   但是可以涉及并且使用到maven 因为maven有很多plugin是存在于云端的，使用时才会访问云端的网站，而云端的网站在访问时，会有fail
    *   需要设定https
    *   具体参考的方法是 : http://3ms.huawei.com/km/groups/3942288/blogs/details/11996165


##  高并发IO底层原理
### IO读写基本原理
***************
**  内核空间 *** => 操作系统相关
***************
**   用户空间 ** => 只能执行简单的运算
*************** 
####    基本原理总结（foucus on 缓存）
*   应用程序的IO操作 == 缓存的复制
*   底层的读写交换 based on 操作系统内核（Kernel）来完成的
*   它们在输入（Input）和输出（Output）维度上的执行流程是类似的，都是在内核缓冲区和进程缓冲区之间进行数据交换
####    为什么要设置这么多的缓存区？
*   减少与设备之间的频繁物理交换
*   缓存区达到一定的数量，IO中断 => 实际IO
*   socket 请求响应案例
    *   客户端发送请求 
        *   write系统调用，数据复制到内核缓冲区
        *   客户端网卡把内核缓冲区请求数据发出
        *   服务端，接收网卡读取到服务端内核缓冲区
        *   服务端：内核缓冲区 => 进程缓冲区
        *   服务端：在用户空间完成客户端的请求所对应的业务
        *   服务端：把响应数据从用户缓冲区 => 内核缓冲区 / write系统调用
        *   发送服务端：将内核缓冲区数据写入网卡，网卡通过底层通信协议发送给目标客户端

### 四种主要的IO模型
*   同步阻塞IO
    *   概念：用户空间主动发起（同步），需要等待内核IO操作彻底完成后才返回用户空间的IO操作，发起IO请求时用户进程处于阻塞状态
*   同步非阻塞IO
    *   用户进程主动发起，不需要等待内核IO操作彻底完成IO操作，在IO操作过程中，发起请求的用户进程处于非阻塞状态
    *   同步非阻塞IO的特点是应用程序的线程需要不断地进行IO系统调用，轮询数据是否已经准备好如果没有准备好就继续轮询，直到完成IO系统调用为止。
    *   总结一下就是轮询 但是用户进程可以不受打断做自己的事情
*   IO多路复用
    *   新系统调用
        *   查询IO文件描述符就绪状态
        *   select/poll系统调用
        *   一旦就绪（可读/可写） => 用户空间根据相应的IO系统调用
        *   经典Reactor模式实现
    *   举个例子讲述IO多路复用
        *   选择器注册 => 将需要read操作的目标文件描述符提前注册到Linux的select和epoll选择器里
        *   就绪状态轮询 => 任何一个socket就绪后就加入列表中
        *   根据列表中的socket发起read调用，用户线程阻塞
        *   复制完成后，内核返回结果
    *   多路复用的特点
        *   一个选择器查询线程可以同时处理成千上万的网络连接
            *   用户不必创建大量线程，也不必维护这些线程，减少了系统的开销
        *   Java的NIO组件使用的是IO多路复用模型
*   异步IO
    *   内核空间成为主动调用者
    *   用户进程收到进程的时候，数据已经被内核读取完毕放在了用户缓冲区
        *   用户发起read系统调用
        *   内核准备数据，然后把数据从内核缓冲区复制到用户缓冲区
        *   内核给用户线程一个信号(Signal)
        *   用户线程读取用户缓冲区的数据
    *   可惜的点
        *   由于当下高并发的服务端的程序都是基于Linux，而这个异步IO需要操作系统支持。所以现在还是常用IO多路复用

####    通过合理配置来支持百万级的并发连接
*   解除句柄数的限制
    *   Linux系统中的默认值是1024
    *   等效含义是一个进程最多有1024个socket连接
    *   ulimit -n 1000000

####    Java NIO
#####   NIO vs OIO
*   OIO是面向流的，NIO是面向缓冲区的
    *   流的读取是有顺序的，不能改变读取指针的位置。NIO引入了Channel 和 Buffer的概念，可以随意读取Buffer任意位置的数据
    *   OIO操作是阻塞的，NIO的操作是非阻塞的。
    *   OIO没有选择器的概念，而NIO有选择器的概念
*   通道
    *   OIO中同一个连接包括输入流和输出流
    *   NIO中一个网络连接使用一个通道表示，所有操作都可以用通道来完成
*   选择器：用一个进程、线程可以同时监视多个文件描述符
*   缓冲区即Buffer
######  详细讲解NIO Buffer
*   本质上是一个内存块，既可以写入数据，也可以读取数据
*   NIO Buffer提供了一组比较有效的方法，来进行写入和读取的交替访问
*   Buffer 是一个 非线程安全类
*   本质上是一个抽象类
######  Buffer类重要属性
*   拥有一块内存作为数据的读写缓冲区，定义在具体的子类里面
*   capacity
    *   写入对象的最大限制数量，并且数组分配好了以后大小就不能改变了
*   position
    *   读写模式都类似于先变成0，再逐渐增加然后读取
*   limit
    *   读写情况下表达的意思有区别
*   涉及的函数包括
    *   allocate    分配空间
    *   put         新加变量
    *   flip    翻转(写<=>读模式)
    *   get        按照position 来读取
    *   rewind      倒带(position回到初始0位置)
    *   reset       会让position回到mark的位置
    *   mark        记住当下position以便之后跳转
    *   clear       完全清空
*   集合体代码
    *   UseBuffer系列代码

#####   详细解释NIO Channels
*   4种channel
    *   FileChannel : 文件通道，文件数据的读写
    *   SocketChannel ：套接字的通道，TCP连接的数据的读写
    *   ServerSocketChannel : 服务器套接字通道，监听TCP连接请求
    *   DatagramChannel :数据报通道，用于UDP的数据读写

*   File Channel流程图
    *   创建文件流，输入流输出流
    *   获取inChannel和outChannel
    *   Buffer初始化此时为写模式
    *   模式翻转，Buffer转化为读，并且从inChannel读取数据到buf
    *   Buffer写入输出通道
    *   Buffer清除，清除buf,变成写模式
    *   强制刷新到磁盘

|ServerSocketChannel|SocketChannel|
|-------------------|-------------|
|    连接的监听        |      涉及连接数据的传输      |
|        服务端            |       服务端，用户端       |


#####   NIO Selector
*   选择器与注册
    *   选择器是为了完成IO多路复用,主要是为了注册、监听、事件查询
    *   通道和选择器之间的关联通过register完成
    *   IO事件
        *   表示通道具备执行某个IO操作的条件
*   SelectableChannel
    *   如果继承SelectableChannel那么该通道就能被选择
    *   SelectionKey类似于名单，把所有就绪的IO事件都放入了SelectionKey
*   Selector流程
    *   获取选择器 => 获取通道 => 设置为非阻塞 => 绑定连接 => 将通道注册到选择器上 => 轮询感兴趣I/O就绪事件 => 获取选择键集合 => 获取单个选择键并处理 => 判定key并且获取客户端新链接 
*   Buffer相关代码
```java

import java.nio.IntBuffer;

public class UseBuffer {

    static IntBuffer intBuffer = null;
    public static void allocateTest()
    {
        intBuffer = IntBuffer.allocate(20);
        System.out.println("-------------------------After allocate--------------------\n");
        System.out.printf("posttion=%d\n",intBuffer.position());
        System.out.printf("limit=%d\n",intBuffer.limit());
        System.out.printf("capacity=%d\n",intBuffer.capacity());
    }
    public static void putTest()
    {
        for(int i = 0; i < 5 ; i++)
        {
            intBuffer.put(i);

        }
        System.out.println("-------------------------After putTest--------------------\n");
        System.out.printf("posttion=%d\n",intBuffer.position());
        System.out.printf("limit=%d\n",intBuffer.limit());
        System.out.printf("capacity=%d\n",intBuffer.capacity());
    }
    public static void flipTest()
    {
        intBuffer.flip();
        System.out.println("-------------------------After flipTest--------------------\n");
        System.out.printf("posttion=%d\n",intBuffer.position());
        System.out.printf("limit=%d\n",intBuffer.limit());
        System.out.printf("capacity=%d\n",intBuffer.capacity());
    }
    public static void getTest()
    {
        //先读取2个数据
        for(int i = 0;i<2;i++)
        {
            int j = intBuffer.get();
            System.out.println("j = " + j);
        }
        System.out.println("-------------------------After get 2 int--------------------\n");
        System.out.printf("posttion=%d\n",intBuffer.position());
        System.out.printf("limit=%d\n",intBuffer.limit());
        System.out.printf("capacity=%d\n",intBuffer.capacity());
        for(int i = 0;i<3;i++)
        {
            int j = intBuffer.get();
            System.out.println("j = " + j);
        }
        System.out.println("-------------------------After get 3 int--------------------\n");
        System.out.printf("posttion=%d\n",intBuffer.position());
        System.out.printf("limit=%d\n",intBuffer.limit());
        System.out.printf("capacity=%d\n",intBuffer.capacity());
    }
    public static void rewindTest()
    {
        intBuffer.rewind();
        System.out.println("-------------------------After rewind--------------------\n");
        System.out.printf("posttion=%d\n",intBuffer.position());
        System.out.printf("limit=%d\n",intBuffer.limit());
        System.out.printf("capacity=%d\n",intBuffer.capacity());
    }
    public static void reRead()
    {
        for(int i = 0;i < 5;i++)
        {
            if(i == 2)
            {//标记第三个位置
                intBuffer.mark();
            }
            int j = intBuffer.get();
            System.out.println("j = " + j);
        }
        System.out.println("-------------------------After reRead--------------------\n");
        System.out.printf("posttion=%d\n",intBuffer.position());
        System.out.printf("limit=%d\n",intBuffer.limit());
        System.out.printf("capacity=%d\n",intBuffer.capacity());
    }
    public static void afterReset()
    {
        intBuffer.reset();
        System.out.println("-------------------------After reset--------------------\n");
        System.out.printf("posttion=%d\n",intBuffer.position());
        System.out.printf("limit=%d\n",intBuffer.limit());
        System.out.printf("capacity=%d\n",intBuffer.capacity());
        for (int i=2;i<5;i++)
        {
            int j = intBuffer.get();
            System.out.println("j = " + j);
        }
    }
    public static void clearDemo()
    {
        System.out.println("-------------------------After clear--------------------\n");
        intBuffer.clear();
        System.out.printf("posttion=%d\n",intBuffer.position());
        System.out.printf("limit=%d\n",intBuffer.limit());
        System.out.printf("capacity=%d\n",intBuffer.capacity());
    }
    public static void main(String[] args) {

        allocateTest();

        putTest();
        flipTest();
        getTest();
        rewindTest();
        reRead();
        afterReset();
        clearDemo();
    }

}
```

*   FileChannel相关代码
```java
import java.io.File;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.nio.ByteBuffer;
import java.nio.channels.FileChannel;


public class FileNIOCopyDemo {
    public static void main(String[] args) {
        nioCopyResourceFile();
    }
    public static void nioCopyResourceFile()
    {
        String sourcePath = "./1.txt";
        String srcPath = sourcePath;
        String destPath = "./2.txt";
        String destDecodePath = destPath;
        nioCopyFile(srcPath,destDecodePath);
    }
    public static void nioCopyFile(String srcPath, String destPath)
    {
            File srcFile = new File(srcPath);
            File destFile = new File(destPath);
            try
            {
                if(!destFile.exists())
                {
                    destFile.createNewFile();
                }
                long startTime = System.currentTimeMillis();
                FileInputStream fis = null;//文件输入流
                FileOutputStream fos = null;//文件输出流
                FileChannel inChannel = null; //输入通道
                FileChannel outchannel = null; //输出通道
                try {
                    fis = new FileInputStream(srcFile);
                    fos = new FileOutputStream(destFile);
                    inChannel = fis.getChannel();
                    outchannel = fos.getChannel();
                    int length = -1;
                    //新建buf，处于写模式
                    ByteBuffer buf = ByteBuffer.allocate(1024);
                    //从输入通道读取到buf
                    while ((length = inChannel.read(buf)) != -1) {
                        //buf第一次模式切换：翻转buf，从写模式变成读模式
                        buf.flip();
                        int outlength = 0;
                        //将buf写入输出的通道
                        while ((outlength = outchannel.write(buf)) !=
                                0) {
                            System.out.println("写入的字节数：" +
                                    outlength);
                        }
                        //buf第二次模式切换：清除buf，变成写模式
                        buf.clear();
                    }
                    //强制刷新到磁盘
                    outchannel.force(true);
                } finally {
                    //关闭所有的可关闭对象
                    //IOUtil.closeQuietly(outchannel);
                    //IOUtil.closeQuietly(fos);
                    //IOUtil.closeQuietly(inChannel);
                    //IOUtil.closeQuietly(fis);
                    System.out.printf("finished");
                }
                long endTime = System.currentTimeMillis();
                System.out.println("base复制毫秒数：" + (endTime - startTime));
            } catch (IOException e) {
                e.printStackTrace();
            }

                    }
}



```





#####   Reactor模式
*   Nginx 和 Redis就是基于Reactor模式
*   Reactor模式
    *   Reactor 线程 : 负责响应IO事件,分发到IO事件
    *   Handlers 处理器 : 非阻塞地执行业务处理逻辑
*   初始版本
    *   多线程OIO致命缺陷
        *   堵塞
        *   选择Connection Per Thread 模式,较高地提升了服务器的吞吐量
*   单线程Reactor —— 版本之子 
    *   类似于事件驱动模式，当有事件触发时，事件分发到Handler，由Handler负责事件的处理。
    *   Reactor 和 Handlers处于一个线程运行
        *   Reactor负责查询IO事件，检查到一个IO事件时将其发送到对应的Handler处理器去处理。(这里的IO事件就是NIO中选择器查询出来的通道IO事件)
        *   Handler：与IO事件绑定，负责IO事件的处理，完成真正的连接建立、通道读取、处理业务逻辑、负责将结果写到通道
*   简单的单线程版本Reactor
    *   attach
    *   attanchment
*   单线程Reactor参考代码
*   多线程Reactor模式
    *   升级的Handler，既要使用多线程，又要尽可能高效率，使用到了线程池
    *   Reactor也升级了，考虑引入了多个Selector选择器，提升选择大量通道的能力
    *   如果服务器是多核的CPU，可以将反应器线程拆分成多个子反应器
    *   ![多线程Reactor](../Chenzhuang/1.png)

####    模式对比
*   Reactor vs 生产者消费者模式
    *   实际原理类似
    *   但是Reactor基于查询，而生产者消费者是有一个存各类IO事件的缓存队列
*   Reactor vs 观察者模式
    *   Reactor 分发以后，会绑定一个Handler
    *   而观察者模式，又称发布/订阅模式，一个主题可能被多个观察者发现，并通知到
*   Reactor缺点
    *   复杂
    *   依赖于IO多路复用调用，比如Linux的epoll系统调用
    *   在同一个Handler的业务流程中，如果出现同一个长时间的数据读写就会影响这个反应器的其他通道的IO处理
