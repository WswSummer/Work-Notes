用Elastic Search搭建全文索引也通常被称为“数据库搜索”。绝大多数现代关系数据库并不以处理文本搜索为核心功能，所以日常应用中通常需要将Elastic Search与Postgres, MySQL之类的数据库一起使用。

而把这 10 万 T 的数据，分成一个 T 一个 T，放在 10 万台服务器上的过程，就是分布式数据库中常见的名词：分片（英文叫 sharding）。

当数据量太大，单机无法处理，这时在分布式服务中常见的一个手段就是分片，把数据拆成一个个独立的单元，放到不同服务器上。再在程序里把这些数据组织起来。

一个集群中，抽象地会有 N 个节点，这些节点，可以简单地想象成服务器的概念。

当你的数据量越来越多时，因为一个节点装不下你的数据，你会开始需要做分片，做所谓的横向扩展

比如说，我们用一个已经非常大的公司——小红书，做例子。Google 索引了小红书 1200 万的页面，我们再假设每个页面都是字数 1000 个左右的汉字，那么这一千多万个页面全部存起来的话，不过24G左右。即使是用相对复杂一点的索引方法（关于索引，后文会讲）也不会超过 500G。因此，对绝大多数公司来说，业务数据要达到开始分片的规模，其实是少见的。当然，数据产生（比如爬虫公司）或者专门的数据搜集公司除外。

![google索引的小红书页面量](https://kalasearch.cn/static/f6699da1f298ed97f9ef7bd225813108/5a190/google-indexed-xiaohongshu.png)

在 Elastic Search 中，我们把同样的数据放在多个服务器上这样的配置叫副本分片（replica），而一个集群同样需要知道各个副本分片的信息。这样，集群的另一个作用就是用来管理副本分片。

ES节点：

- 主节点（master-eligible node）负责各种沟通协作节点的工作，一个集群必须有至少一个
- 数据节点（data node）主要负责搜索和数据存储
- 写入节点（ingest node）主要负责文档写入

真正在日常开发中会直接打交道的概念——索引

**索引**的概念可以简单理解为，一系列文档的集合（下文我们继续深入讲什么是文档，这里你先理解，文档就是你往搜索引擎里存的每一行数据，比如如果要搜索商品的话，就是一件商品的信息）。

搜索引擎之所以可以非常快速地找到包含你键入的关键词的文章，就是因为索引的巧妙存储结构。

简单地说，假设我们有一万篇文档，你有一个关键词是 `熊猫`，那么最笨的办法无非是把这一万篇文档全看一遍扫一遍，找出来哪些文档含有熊猫这个词。

然而有一种特殊的数据结构（值得单独开一篇详讲）叫作**倒排索引**（invereted-index），**它的作用是提前先处理一个映射，可以让你快速地从一个词，找到这个词在你的这些文档里对应的所有文档编号。**

![倒排索引的例子](https://kalasearch.cn/static/50d831e7eea814c546148bd05d95393a/80e3c/inverted-index.jpg)

比如在上图中，假设我们有200篇文章，编号从1到200。这200篇文章中有各种各样的词语，比如说 `Peiking University`, `Stanford`等等。举个例子，其中一篇文章编号3可能是

```text
Peiking University is one of the best universities in China,
while Stanford is one of the best in the United States.
```

那么我们说，我们的索引就包含200篇文章。而对于我们的这个索引，其存为倒排索引的结构则为上图所示：

对于词语`Stanford`，它在这个索引对应的倒排索引中，含有的文档就有上述的文档3，8，10，13，16和20.

那么当你要搜索 `Stanford University` 这个短语的时候，查看一下倒排索引，可以瞬间找出含有 `Stanford` 的文档的列表。同样的道理，你再把含有 `University` 这个短语的列表，全部找出来。两者相交一下，即可找出有短语`Stanford University` 的所有文档。

虽然 Elastic Search 本身是个巨兽，但是其 20 余万行代码里，几乎全部是为搜索服务器服务的。而真正处理倒排索引、具体搜索算法的，则是一个叫 `Lucene` 的核心引擎。

关于索引，我们整理一下

1. 一系列文档形成一个索引（Index）
2. 索引在搜索引擎里的具体存储数据结构叫倒排索引（Inverted Index），之所以叫倒排，是因为它是从词语到文档的关系。如果你看技术书的时候翻到最后几页，通常有一个索引列出来一些专有名词和其对应的页码，就跟倒排索引的存储方式很类似
3. ES 用的搜索核心引擎叫 `Lucene`

***

Elastic Search 里的文档输入格式全为 JSON。当你把一个 JSON 文档发给 Elastic Search 的时候，它会先做一系列处理，然后往你指定的索引中插入这个文档。

请注意，你的输入格式为 JSON，但并不代表在Elastic Search内，文档是以 JSON 形式存储的。具体来说，当你往 Elastic Search 里添加一篇文件的时候，发生了以下过程

1. Elastic Search 把 JSON 文档拆开，分析里面的内容，并区分对待文字、字符串、日期等格式
2. 处理完后 Elastic Search 会把你的文档拆成很多域（即 Field）。比如说，豆瓣电影的数据会有 `电影名`, `演员`，`打分` 这三个域
3. 处理完域后，Elastic Search 会把这些域转为一个 Lucene 文档，然后交给 Lucene 真正地插入到 Lucene 的倒排引擎里
4. 当你在搜索时，Elastic Search 会把你的查询，转换好，交给 Lucene。Lucene 返回的结果再包装一下，还给 Elastic Search，最后返回给用户

***

笔记：

![image](https://user-images.githubusercontent.com/34562805/102298801-c3ed1d00-3f8c-11eb-8a53-5583074d442e.png)

![image](https://user-images.githubusercontent.com/34562805/102298995-2514f080-3f8d-11eb-83de-fe7e5bbbfc82.png)

![image](https://user-images.githubusercontent.com/34562805/102299394-d7e54e80-3f8d-11eb-9cef-8f58b4209fd8.png)

![image](https://user-images.githubusercontent.com/34562805/102325856-a042ca80-3fbe-11eb-9b9f-5f94e4c80d89.png)

![image](https://user-images.githubusercontent.com/34562805/102325957-c1a3b680-3fbe-11eb-8327-cd1adeb7652a.png)

