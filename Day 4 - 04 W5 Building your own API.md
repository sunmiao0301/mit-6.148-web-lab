

# Day 4 - 04 W5: Building your own API

## Build an API!

对比一下endpoint和route，endpoint提供某些特定功能。route是访问endpoint的路径。他们的数量是1：1的。

目前，我们只自己写成了一个/api/test的API，下面我们将写一些更有有用的API，包括可以动态地存储、提取 数据的API。

![image-20220328094729121](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203280947459.png)



## git checkout w5-starter

之前我们将API写在server.js中，导致server.js不可避免的长了，现在我们将新建一个api.js来专门存放我们的api，并通过路由将api.js链接给sever.js



## git checkout w5-step1

下面，让我们写一个真正有用的API，那么首先就是构建一个”数据库“，我们就先不用真正的数据库，而是用let变量模拟一个最简单的数据：（放到api.js中）

```javascript
const MY_NAME = "Anonymous USer";

let data = {
  stories: [
    {
      _id: 0,
      creator_name: "Sun Miao",
      content: "I love zhu!",
    },
  ],

  comments: [
    {
      _id: 0,
      creator_name: "zhu",
      parent: 0,//这里很关键，我们后面就是用它查询的
      content: "I love you, too",
    },
  ],
};
```

让我们分析一下：

```javascript
router.get("/test", (req, res) => {
  res.send({ message: "Wow I made my first API! In its own file!" });
});
```



## req & res

req is the incoming request，有一些方法：

- req.query
- req.body



req is your server's response，有一些方法：

- res.send(<object>)
- res.status(<status code>)



## GET /api/stories

我们将构建一个将数据从后端传向前端的api，如下即可。

```javascript
router.get("/stories", (req, res) =>{
  res.send(data.stories);
})
```

然后我们可以在后端测试一下这个api

![image-20220328110429627](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281104681.png)



## GET /api/comments

需要注意的是，这里与stories不太一样，我们不能直接拿到所有的评论，然后放到一个帖子下，我们得找到某个特定的帖子下面对应的评论，目标如下：

![image-20220328110255188](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281102336.png)

实现如下：

```JavaScript
router.get("/comment", (req, res) =>{
  const filteredComments = data.comments.filter((comment) => comment.parent == req.query.parent);
  res.send( filteredComments );
});

//req.query 其中req.query是一个方法。
```

如此，我们就可以这样访问：

![](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281308233.png)

而如果像下面这样访问，就拿不到结果：

![image-20220328130902933](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281309986.png)



下面我们去看看前端调用后端接口的情况：

## npm run hotloader & npm run start

注意，此时我们已经打开了三个终端，一个用于git，一个用于npm run hotloader访问前端，一个用于npm run start

![image-20220328131456469](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281314624.png)



访问localhost:5000查看前端：

![image-20220328131609911](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281316967.png)



然后我们尝试POST一个帖子，但是没有反应，我们可以inspect，发现出现了报错：Uncaught (in promise) POST request to /api/story failed with error:
API request failed with response status 404 and text: Not Found

![image-20220328131734611](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281317711.png)



## git checkout w5-step2

在完成POST-API之前，我们想要完成一个所有尝试访问其他api都404的报错。—— handing missing API routes —— 并且注意，这段代码应该放到最后。

```javascript
router.all("*", (req, res) =>{
  console.log(`API Route not found: ${req.method} ${req.url}`);
  res.status(404).send("API Route not found!")
});
```

然后我们在前端是访问一个不存在的api：http://localhost:3000/api/yeet，就能看到我们设置的报错信息，以及检查可以看到返回错误的状态码404

![image-20220328133615003](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281336193.png)



## 下面我们将完成POST-API

**首先是GET和POST需要的req区别 —— 当我们在GET的时候，我们的api通过req.query得到后端的值并且显示在前端。当我们POST的时候，我们的api通过req.body来拿到我们在前端输入的值，并且传输到后端：** ![image-20220328133954407](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281339514.png)



## POSt /api/comment

```javascript
router.post("/comment", (req, res) =>{
  const newComment = {
    _id: data.comments.length,
    creator_name: MY_NAME,
    parent: req.body.parent,
    content: req.body.content,
  };

  data.comments.push(newComment);
  res.send(newComment);
})
```



## 悬而未决

可以发现，当我们刷新我们的页面的时候，我们新增的帖子和评论都消失了。这是因为我们的data实际上是定义在我们的server文件（app.js）中的，所以每当我们刷新的时候，我们新发的内容并没有存到代码中，进而消失了。

所以下一节课，我们将开始进入数据库 —— MongoDB！



## 看代码 —— api.js

```JavaScript
/*
|--------------------------------------------------------------------------
| api.js -- server routes
|--------------------------------------------------------------------------
|
| This file defines the routes for your server.
|
*/

// without a system for users, we'll have to hardcode our user name
const MY_NAME = "Hackerman";

const data = {
  stories: [
    {
      _id: 0,
      creator_name: "Shannen Wu",
      content: "I love corgis!"
    }
  ],
  comments: [
    {
      _id: 0,
      creator_name: "Jessica Tang",
      parent: 0,
      content: "Wow! Me Too!",
    }
  ],
};

const express = require("express");

const router = express.Router();

router.get("/test", (req, res) => {
  res.send({ message: "Wow I made my first API! In its own file!" });
});

router.get("/stories", (req, res) => {
  // send back all of the stories!
  res.send(data.stories);
});

router.get("/comment", (req, res) => {
  const filteredComments = data.comments.filter(
    (comment) => comment.parent == req.query.parent);
  res.send(filteredComments)
});

router.post("/story", (req, res) =>{
  const newStory = {
    _id: data.stories.length,
    creator_name: MY_NAME,
    content: req.body.content,
};

  data.stories.push(newStory);
  res.send(newStory);
})

router.post("/comment", (req, res) =>{
  const newComment = {
    _id: data.comments.length,
    creator_name: MY_NAME,
    parent: req.body.parent,
    content: req.body.content,
  };

  data.comments.push(newComment);
  res.send(newComment);
})

router.all("*", (req, res) =>{
  console.log(`API Route not found: ${req.method} ${req.url}`);
  res.status(404).send("API Route not found!")
});

module.exports = router;
```



















