填坑与埋坑
==========

从事spark相关的工作一年快五个月了，但是一直没有去做相关的总结，没有总结就没有沉淀，今天在这里“开贴”，自己挖坑自己埋，在哪一天这里没有坑，或许就是我[秘密](.)

# Spark-Shuffle
包括mapreduce和spark在内的所有离线计算工具，shuffle操作永远是设计最为笨重的，也是整体计算性能的瓶颈。主要原因是shuffle操作是不可避免的，
而且它涉及到大量的本地IO，网络IO，甚至会占用大量的内存，CPU来做sort-based shuffle相关的操作。
这里挖一个这个坑，由于第一个坑，所以我会在这个坑里面阐述大量的spark基础的东西，随便对这些基础做一下整理。

+   开始埋坑日期：2014-9-24
+   期望完成日期：2014-10-7
+   坑状态：doing

# Scala闭包/function/method的研究
scala是一门函数编程语言，当然函数，方法，闭包这些概念也是他们的核心，在阅读spark的代码过程，也充斥着大量关于scala函数相关的特性引用，比如：

    def map[U: ClassTag](f: T => U): RDD[U] = new MappedRDD(this, sc.clean(f))
map函数的应用，每次我传入一个f都会做一次sc.clean的操作，那它到底做了什么事情呢？其实这些都和scala闭包有关系。这里继续埋坑

+   开始埋坑日期:2014-9-25
+   期望完成日期：2014-10-30
+   坑状态：pending

# Spark-Block管理
在Spark里面，block的管理基本贯穿了整个计算模型，从cache的管理，shuffle的输出等等，都和block密切相关。这里挖一坑，这个坑填好的时候，也许spark也就通了。

+   开始埋坑日期:2014-9-25
+   期望完成日期：2014-10-20
+   坑状态：pending

# RPC
## thrif
一个完美集成序列化和RPC通信的跨语言通信框架，用起来实在是方便，但是没有对它Protocal,Transport,Model等实现研究一下，也让人很不踏实。  
这里挖一个坑，对thrift进行深入研究一下。

+   开始埋坑日期:2014-9-25
+   期望完成日期：2014-11-30
+   坑状态：pending

## hadoop-rpc
thrift是一个很好的RPC框架，但是Hadoop的基于writable和protocal实现的两个版本的RPC框架其实也很牛，前后以后看了三次，都是一不总结就忘记了，这次RPC坑一起总结了。

+   开始埋坑日期:2014-9-25
+   期望完成日期：2014-11-30
+   坑状态：pending

## akka
与thrift，hadoop实现RPC的逻辑不通，spark基于akka来进行RPC通信，不说了，这个东西真心好用，而且好像是基于协程来做，找一周时间深入研究一下，

+   开始埋坑日期:2014-9-25
+   期望完成日期：2014-11-30
+   坑状态：pending

#   列存储
到目前为止接触了RCFile，ORC, Parquet三种列存储的离线数据存储结构，虽然都有接触，但是还是研究不够彻底，这里挖坑，填好。

+   开始埋坑日期:2014-9-25
+   期望完成日期：2014-10-30
+   坑状态：pending

#   hive执行过程
这次解决hive小文件过程，终于把hive的执行过程过了一边，这里简单做一个记录，这个坑不深挖，怕填不懂，特别语法解析那块，没有太多时间，精力，还有能力去填

+   开始埋坑日期:2014-9-25
+   期望完成日期：2014-10-30
+   坑状态：pending

#   hive小文件
namenode被hive小文件搞的不行了，这次算是定位到这个原因了，这里挖个坑，找个时间总结一下

+   开始埋坑日期:2014-9-25
+   期望完成日期：2014-10-30
+   坑状态：pending

#   spark调试系统的开发
这是一个代码坑，算是自己第一个开源程序，简单的想法就是在spark应用程序正式发布之前，可以通过这个系统进行调试，了解任务运行过程，资源占用情况，
从而可以分析出未来正式上线需要分配多少资源。

+   开始埋坑日期:2014-9-25
+   期望完成日期：2015-1-30
+   坑状态：pending
