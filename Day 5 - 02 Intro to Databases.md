# Day 5 - 02 Intro to Databases

 ![image-20220328162443075](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281624235.png)



前后端如何协同？

对于post：

![image-20220328162837450](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281628598.png)

对于get：

![image-20220328162932887](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281629023.png)



## Intro to database

为什么需要数据库？假设我们将数据以变量形式存储在服务器上，如下：

![image-20220328163326203](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281633305.png)

然后不幸的是，服务器宕机，等到重启的时候，服务器中所有的变量都丢失了：

![image-20220328163359624](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281633752.png)



## What's wrong with storing data in a variable on the server?

这种做法除了会在以下四种情况的时候丢失信息，还有很多需要面对的问题，比如:

- 如果catbook有大量用户，那么你需要存储多少帖子和评论在你的电脑memory RAM中？

![image-20220328163854662](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281638796.png)



## We need to store our data permanently

所以我们需要想到一种永久存储我们数据的办法：

- data.txt 文本文件怎么样？ —— git c heckout textfile

  可以，但是有什么问题？

  ![image-20220328164654501](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281646677.png)

- 怎么解决？

![image-20220328164924779](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281649881.png)

*p.s. MySQL与MongoDB都是开源的常用数据库，但是MySQL是传统的关系型数据库，MongoDB则是非关系型数据库，也叫文档型数据库，是一种NoSQL的数据库。 它们各有各的优点，关键是看用在什么地方。 所以我们所熟知的那些SQL语句就不适用于MongoDB了，因为SQL语句是关系型数据库的标准语言。*



## 增删改查

![image-20220328165305974](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281653172.png)



## What kind of database can I use?

- 关系型数据库 —— MySQL...
- Document Database（NO SQL） —— 存储文档，基于JSON对象。—— we will be using this! you are already familiar with JSON.

![image-20220328165740298](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281657471.png)

 

## We will run MongoDB in the cloud, using Atlas

Later, Writing code with MongoDB, Good luck in Workshop 6!



















