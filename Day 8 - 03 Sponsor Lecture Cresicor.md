# Day 8 - 03 Sponsor Lecture: Cresicor



## first question：How would you represent this in a database?

![image-20220402131423768](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204021314929.png)

 

## first solution -- JSON

json本质上是数据字典，如下：

![image-20220402132343599](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204021323767.png)

但当数据量更大的时候，我们怎么提高性能?

## 可以简化数据表示 —— 此时size of data是 138 bytes

![image-20220402132906180](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204021329334.png)

在此基础上，怎么做一些更基础、更根本的变化？

## SQL verses NoSQL

Our purpose here is to present how different databases can address different use cases.

### 首先考虑，如果下面的数据要存储在关系型数据库中，该怎样？  

![image-20220402134759234](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204021347364.png)

会变成下面这样：

## SQL —— 此时size of data是 115 bytes

![image-20220402135405997](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204021354132.png)

上面的优势在于：

![image-20220402140252355](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204021402501.png)

劣势在于：

1）这样的数据不是我们从网络中拿到的最原始的JSON格式了，而是从JSON格式被转化为table的样式存储到table样式的SQL数据库中，即使是对我们上面的数据而言，这样的转变也需要三层for循环来完成，这样的过程是耗时的，我们为什么不一开始就考虑以JSON形式存储呢？

2）关系型数据库的代码更难写



## 最终总结

1）那些随着时间，而不断变化、演变的情况下，NoSQL更好，因为我们可以方便的不断加入新Schema

2）但如果你需要以表格形式存储数据的时候，数据量更大，且事先确认不会更改架构的情况下，SQL更好。











