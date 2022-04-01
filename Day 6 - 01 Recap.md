# Day 6 - 01 Recap

 

Client -- Frontend code：The code that is in front of you. —— **注意，JavaScript也属于前端的东西**

Server -- Backend code：The code that is behind that scenes.

下面是前后端的一个小总结：

![image-20220331171347484](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311713636.png)

以及他们在前后端代码的体现：

![image-20220331171515675](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311715946.png)

## meme

![image-20220331171928023](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311719272.png)

## 以及

![image-20220331172020705](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311720839.png)

**注意，ReactJS和NodeJS都是使用的JavaScript代码，也是编写JavaScript的不同方式。**

  

## React

**Props是可以传递的，但State是由一个组件维护的。**



### 关于数据更新

1）异步 所以加上then

2）React will re-run when props or states change 所以加上 useEffect



## 关于webapp的设计

![image-20220331173421835](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203311734072.png)

下面举个简单的例子，比如一个公共聊天室如下。

![image-20220401100955831](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204011009953.png)

那么根据上面的四个步骤，我们应该：

1）第一步，确定你应该在数据库中存储什么数据，这个公共聊天室很明显只有一种需要存储的数据：消息 -- 由姓名和消息内容组成，所以我们的数据库Schema应该如下：

```javascript
const mongoose = require("mongoose");

const MessageSchema = new mongoose.Schema({
  name: String,
  text: String,
});

module.exports = mongoose.model("message", MessageSchema);
```

2）第二步，服务器需要什么功能？应该是post和get，具体来说，就是Get all the message 和 Post a new message。实现如下：

```javascript
router.get("/allmessages", (req, res) =>{
  Message.find({}).then((messageFromDB) => {
    res.send(messageFromDB);
  });
});

router.post("/newmessage", (req, res) =>{
  const newMessage = new Message({
    name: "Anonymous",
    text: req.body.text,
  });
  newMessage.save();
});
```

3）我们需要哪些React组件？

![image-20220401110314413](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204011103639.png)

4）我们该在哪里前端的哪儿使用get和post？state和props在哪使用？具体如下：

![image-20220401110802148](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204011108299.png)

以及

![image-20220401110818849](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204011108996.png)



## 此外，还有一个小的mini-workshop，要求如下

![image-20220401111034210](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204011110395.png)

其完成版见：git checkout w6-date