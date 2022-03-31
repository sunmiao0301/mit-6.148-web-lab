

# Day 5 - 03 W6: Databases Workshop

## Structure

![image-20220328172938756](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281729889.png)

亦或：

![image-20220328173048017](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203281730143.png)

Each collection should have a schema.



## Mongoose

是一个node.js库，让我们和mongoDB的交互更加容易。—— **wrapper that allows you to interacr with MongoDB API**，也就是说当我们想要对我们MongoDB中的数据进行操作的时候，我们不需要像传统的操作一样，调用MongoDB的post操作等，只需要使用Mongoose，它为我们隐藏了post的实现细节。我们只需调用简单的函数，就可以将我们的对象添加到数据库中。



 ## Mongoose 能做什么？

- 连接到集群 - 本workshop中不会覆盖
- 创建documents
- 与数据库交互 - GET、POST、Edit、Delete、and more！



## 为什么一定要Mongoose？

因为MongoDB本身不会控制alll documents in one collection have the same structure.最终的MongoDB将会变成下面这样：

![image-20220331100831686](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311008907.png)

而Mongoose将会在结构不匹配的时候，引发错误。



## Schema

schema定义了document的所有字段，以及字段的数据类型。 如下左边的schema，那么右边的就可以被存入：

![image-20220331101420105](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311014229.png)



 ## 两步创建一个Mongoose Model

可以看到第二步的两个参数，第一个是model（collection）的名字，第二个参数是这个collection必须遵循的schema，也就是我们在第一步创建的。

![image-20220331102508366](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311025512.png)



## Creating Documents

然后就是在我们创建的collection中创建document。

![image-20220331102930798](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311029948.png)



## All together 

下面是一个总结的、使用MongoDB的全过程：(代码第一行是导入mongoose库)

![image-20220331103306532](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311033681.png)



## Atlas

MongoDB Atlas is **a multi-cloud database service by the same people that build MongoDB**. Atlas simplifies deploying and managing your databases while offering the versatility you need to build resilient and performant global applications on the cloud providers of your choice.

![image-20220331104208625](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311042762.png)



## _id

- 每个document都会被自动分配一个_id
- 当两个document之前存在关系的时候，_id会很有用 —— 定义document之间的关系 —— 链接。（有点像我们之前所说的parent，我们可以通过评论的父级parent来找到对应的帖子）



## Finding Document

document也就是我们常说的对象。

![image-20220331104631752](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311046960.png)



## Deleting Documents

- deleteOne
- deleteMany

![image-20220331104819907](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311048132.png)



## Mongoose Structure

![image-20220331104922252](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311049392.png)



## Workshop：Hook Database to Your Catbook App

- 链接我们之前写好的后端到mongoDB
- 为我们的评论和帖子创建models
- 修改我们的API，让其使用我们的mongoose models



## git checkout w6-starter



### 先决条件

云 MongoDB 就是把 MongoDB 安装在远程的服务器上，并对外暴露一个服务地址，我们用这个服务地址来连接数据库进行操作。我们在workshop6中使用云mongoDB

Azure + HongKong 即可。

到下面这一步的时候，选择第二项 —— connect your application

![image-20220331130643983](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311306215.png)

然后如下即可：

![image-20220331130927667](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311309793.png)

mongodb+srv://sunmiao:<password>@cluster0.wqmzz.mongodb.net/myFirstDatabase?retryWrites=true&w=majorit，并将其中的**<password>**替换为**sunmiao**用户的密码。 将**myFirstDatabase**替换为默认连接将使用的数据库的名称。确保任何选项参数都是[URL 编码](https://dochub.mongodb.org/core/atlas-url-encoding)的。

然后回到catbook-react / server / server.js 的下面行，将我们上面拿到的srv信息放入" "

```javascript
// TODO change connection URL after setting up your own database
const mongoConnectionURL = "";
```

但是当我们启动`npm run start`的时候，却报错如下：

```bash
Error connecting to MongoDB: MongooseServerSelectionError: Could 
not connect to any servers in your MongoDB Atlas cluster. One com
mon reason is that you're trying to access the database from an I
P that isn't whitelisted. Make sure your current IP address is on
 your Atlas cluster's IP whitelist: https://docs.atlas.mongodb.co
m/security-whitelist/
```

这应该是我开了梯的原因"The IP address seen by Atlas is not necessarily the IP address of your workstations. If behind a router that does NAT or using VPN the address seen is the one of the router or the exit point of the VPN. First try to ***Allow Access From Anywhere***. If it works it is most likely because you whitelisted an IP address that is not your public address. Find your public IP with [https://www.whatismyip.com/

为了快速解决，我们可以：（https://stackoverflow.com/questions/62859081/mongodb-could-not-connect-to-any-servers-in-your-mongodb-atlas-cluster-whitel）

1. Click on the Network Access.

[![enter image description here](https://i.stack.imgur.com/f1bNX.png)](https://i.stack.imgur.com/f1bNX.png)

1. Click on the edit button located right next to the delete button.
2. Click on "ADD CURRENT IP ADDRESS" Button and click confirm.

然后重新npm start即可：

```bash
miaosun2@miaosun2 MINGW64 /d/repo/catbook-react (w6-starter)
$ npm start

> catbook-react@1.0.0 start
> nodemon

[nodemon] 2.0.6
[nodemon] to restart at any time, enter `rs`
[nodemon] watching path(s): *.*
[nodemon] watching extensions: js,mjs,json
[nodemon] starting `node server/server.js`
Server running on port: 3000
Connected to MongoDB
```

可以看到Connected to MongoDB



## 开始与MongoDB相关的编码 —— Create Comment and Story Mongoose Models

首先是根据我们后端的需求，建立Stories和Comments。

### 打开models文件夹，进入story.js文件。

根据我们之前的介绍，id字段不需要我们创建，MongoDB会为我们默认生成，所以我们的story schema就只需要创建两个字段即可，我们的代码应该如下：

```javascript
const mongoose = require("mongoose");

//define schema
const StorySchema = new mongoose.Schema({
    creator_name: String,
    content: String
});

module.exports = mongoose.model("story", StorySchema);
```

### comment.js

```javascript
const mongoose = require("mongoose");

//define schema
const CommentSchema = new mongoose.Schema({
    // _id field is autogenerated by Mongoose
    creator_name: String,
    parent: String, // links to the _id of the parent
    content: String
});

module.exports = mongoose.model("comment", CommentSchema);
```



## git checkout w6-step1（记得复制svr信息 —— 为了连接到MongoDB）

编写新的API，进入api.js，为了联系到我们之前写好的models/comment.js和story.js，我们需要在api.js中加入：

```javascript
// import models so we can interact with the database
const Story = require("./models/story")

const Comment = require("./models/comment")
```



## Get all the stories via GET /stories -- return ALL the stories saveed in the database.

```javascript
router.get("/stories", (req, res) => {
  //retrieve our stories from our DB
  Story.find({})//this line could be used to filter
      //wait until I receive all of my stories and then send it back to the frontend / API caller
      .then( (stories) => res.send(stories) );
});
```



## POST /stories

```javascript
router.post("/story", (req, res) => {
  const newStory = new Story({
    creator_name: "miao",
    content: req.body.content,
  });
  newStory.save().then((story) => res.send(story));
});
```



## git checkout s6-step2

然后进行comment的get和post的api的编写（p.s. 注意get和post的req.query 和 req.body的区别）

## get

```javascript
router.get("/comment", (req, res) => {
  //get all of the comments from a specific story
  Comment.find({ parent: req.query.parent } ).then((comments) => {
    res.send(comments);
  });
});
```

## post

```javascript
router.post("/comment", (req, res) => {
  const newComment = new Comment({
    creator_name: "miao",
    content: req.body.content,
    parent: req.body.parent,
  });
  newComment.save().then((comment) => res.send(comment));
});
```

## 编写完以上部分，就可以测试一下了（到localhost:3000 / 5000 测试我们的发帖和评论功能）—— 并且应该可以在我们的云端数据库看到我们发帖和评论的数据。

- post story 和 get story，前端结果如下：

![image-20220331154935778](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311549883.png)

- 数据库结果如下

![image-20220331154740275](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311547012.png)

- 评论的post和get功能，前端如下

![](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311553649.png)

- 数据库结果如下：

![image-20220331155452605](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311554758.png)

功能没什么问题。***p.s. 唯一的问题在于每次调用api进行功能的之后，前后端就会崩掉。必须重启npm start 和npm run hotloader 才能看到结果，报错信息如下：***

后端报错为：

```bash
[nodemon] app crashed - waiting for file changes before starting...
      }
    },
    operationTime: Timestamp { _bsontype: 'Times
stamp', low_: 17, high_: 1648713107 }
  }
}
```

前端报错为：

```bash
 (nampi/errors.html#errors_common_system_errors)
<e> [webpack-dev-server] [HPM] Error occurred while proxying 
request localhost:5000/api/stories? to http://localhost:3000/
 [ECONNREFUSED] (https://nodejs.org/api/errors.html#errors_co
mmon_system_errors)
```



## Recap

- 理解MongoDB的structure、schemas、models
- 链接MongoDB云上的数据库实例到nodejs上的app上 - svr
- 通过api与数据库交互 - post get
- 前端调用api显示数据库中的数据 - get



