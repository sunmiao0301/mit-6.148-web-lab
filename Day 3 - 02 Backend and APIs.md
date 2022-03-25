# Day 3 - 02 Backend and APIs

client and server —— 它们之间的通信采用请求和响应的形式（客户端向服务器发出请求，服务器有望对我的请求做出响应）

 

## 什么是HTTP？

http = hypertext transfer protocol = 超文本传输协议

让我们看一下HTTP的结构：

![image-20220325100050212](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251000307.png)

你将会看到req.body 和 req.query

比如我们当前正在看的视频的链接是：

https://www.youtube.com/watch**?v=zIA3U9QtRmg**

注意?之后的部分就是req.query，这部分就是告诉服务器，我们要拿到的video具体是哪个。

## 

## HTTP Method （request）

常见的方法如下：

![image-20220325100416263](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251004386.png)

GET —— 查

POST —— 增

PUT —— 改

DELETE —— 删



## Responses

状态码 —— 1xx、2xx、3xx、4xx、5xx，用于反馈你的请求request的去向。

比较经典的比如：

404 —— 服务器响应代码，表示无法找到你想要查找的内容。

200 —— ok，应该是最常见的代码，表示找到了你想要的东西，也正因为如此，所以你不会看到这个代码，而是直接看到你请求访问的东西了。

500 —— 服务器内部错误

400 —— Bad Request



以上是一些常见的情况，总计一下也有规律：

![image-20220325101113382](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251011514.png)



## Your request are just out of sigth...

所以让我们尝试去访问它，看到我们一个请求的状态码：

1）随便chrome中打开一个网络页面，然后 ctrl + shift + i

2）然后看里面的 Network 标签

3）然后刷新这个页面，可以看到在Network中进行了大量的工作，并且Status都是200（成功）

![image-20220325101810516](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251018692.png)

4）上面的方法很有用，我们后面进行Web开发的时候需要用到这些。



## APIs

API = Application Program Interface

通常是一系列服务（允许你访问的），比如Google、Amazon和Facebook都提供了一系列API，让你请求服务。—— 形成一种结构化的方式让你请求这些数据。

 ![image-20220325103431753](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251034862.png)



以某家小餐馆为例子，我们可以看到餐馆的界面上内嵌有一个Google地图，但是这家餐馆很显然不是Google公司的，那么它实际上就是调用内嵌了Google的API。

![image-20220325103609021](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251036115.png)



下面是一些很酷的API的例子：

1）Google Maps

2）The Dog API（https://api.thedogapi.com/v1/images/search），这个API每次都会随机返回一个狗的图片给你。

3）https://openai.com/api/ —— Build next-gen apps with OpenAI’s powerful models.



## Swagger

Swagger —— 作为一个api的开发工具界面。

https://petstore.swagger.io/?_ga=2.169913504.1665236147.1578346423-534490964.1578346423#/

![image-20220325104847211](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251048312.png)



以上，就是关于服务器和API的一些简短重点。





