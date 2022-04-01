# Day 4 - 03 NodeJS & Setting Up the Server

设置一台你的服务器

- File access 
- Centralization —— 所有人访问同一页面，看到的东西是一样的。
- Security —— inspect能看到一些源代码，这是不安全的，其次是账号权限问题等。



## Processes & Ports

A server binds to a port on a computer.

如果还记得，我们在之前访问npm run hotloader的时候，就是localhost:5000，其中5000就是端口号。但是在实际中，我们访问的方式是：**一个协议 + 域 + 端口，比如 protocol://domain:port**，其中，协议通常是http https

但是，我们访问Google的时候往往是：google.com 而没有加上特定端口，这其实是因为我们正在隐式访问某些特定端口。

我们的私人电脑也有自己的特有域：localhost。



## 服务器端的代码由什么语言写成？

- python —— 写成Flask、django
- java —— Apache
- javascript —— ExpressJS



可惜，本节课上，不使用java。

![image-20220327225723360](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203272257613.png)

- Node runs JavsScript on your machine
- Express allows you to structure your javascript



## npm —— Node Package Manager (npm)

导入外部库 —— 比如我们之前写前端的时候用的 import React ...，以及我们npm install的时候，实际上是下载了一些json文件和一个node_modules，其中，json文件是为了holds project metadata，而node_modules则是包含了一些依赖（我们在项目中直接使用的外部代码）

![image-20220327230433509](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203272304653.png)



由于后面我们将进行前后端的学习，所以我们需要搞清楚我们代码文件的结构和作用，如下：

## git checkout w4-starter

![image-20220327230626815](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203272306939.png)



## Creating our first API endpoint —— git checkout w4-step1

我们可以在server.js中写下如下接口：**（其中，get是http的方法之一）**

```javascript
app.get("/api/test", (req, res) => {
  res.send({message: "congratulations!"});
});
```

然后运行app.js，然后访问localhost:3000/api/test，可以看到如下结果：

![image-20220327233220207](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203272332278.png)



## Adding Error Handing —— git checkout w4-step2

```javascript
// any server errors cause this function to run
app.use((err, req, res, next) => {
  const status = err.status || 500;
  if( status === 500 ){
    // 500 means Internal Server Error
    console.log("The server errored when processing a request");
    console.log(err);
  }

  res.status(status);
  res.send({
    status: status,
    message: err.message,
  });
});
```



## Saving React Files

我们可以看到，当我们访问一个我们未定义的endpoint，比如localhost:3000/test，我们会看到一个无法从这个endpoint处get到东西的显示。此外，还会得到一个错误代码404，如下：

![image-20220327234925767](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203272349886.png)

但是如果你经常接触到一些网站的404情况，你会发现他们都是有页面的，而不是Cannot GET ...我们要做的就是在遇到404的时候返回一个特定的页面，比如google：

![image-20220327235442177](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203272354236.png)



关于404处理的代码，见git checkout w4-step3



## 接下来是关于顺序，顺序很关键！

下面的图中，左边good，右边bad！当服务器收到请求的时候，它会从你写的第一个端点按顺序从上而下匹配。

![image-20220328001033564](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203280010752.png)

## 5000 还是 3000？

![image-20220328001343876](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203280013433.png)





















