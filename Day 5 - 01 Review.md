# Day 5 - 01 Review

## Website have a frontend and a backend, where the server lives to handle API calls

![image-20220328142210780](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281422971.png)



## React allows you to structure your web development code.

![image-20220328143353223](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281433454.png)



## What is a server?

Just remember: server is another computer and you can get data from it.



## What is the need for a server?

- file access —— 不是所有的数据我们都需要，并且展示在前端，我们需要一个地方去存储它，那就是服务器
- centralization —— 如果没有一个中心化的服务器，那么所有的客户端彼此都需要互相通信，来保证他们访问的页面一致。
- security —— 服务器中的代码不能被任何用户访问，而其他地方的代码很容易受到攻击。



## HTTP

一种协议，是客户端和服务器之间通信的方法。

- GET Request
- POST Request



## API

API是一系列规则，它们描述了如何从服务器得到数据。API endpoint是一系列你可以访问的函数。如下，我们可以通过get函数得到我们想要的结果。

![image-20220328150207730](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281502873.png)



## 异步函数

**JavaScript是一种异步编程语言，也就是可以在运行后面的代码时，还尚未运行前面的代码。—— 原因是我们在JavaScript中经常需要访问其他服务器api等，那么如果不是异步的，如果有一个api访问卡住了，就会到导致后面的都没法运行了。**

**但是这也同时导致了：**

![image-20220328151631692](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281516844.png)

代码的输出是unknown，因为get需要时间，运行是异步的，所以我们会先得到unknown

**这里涉及到then() 也称为 promise**

同理，下面这一题的代码也就是No guarantee

![image-20220328153242479](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281532582.png)



## Coming Up

- Kahoot --> Review
- Databases
- Authentication
- Sockers
- Deployment
- & more advanced topics!



  

 











