# Day 6 - 03 W8: Chatbook -- Sockets Part 1

## 如果你想要实时更新和游戏聊天 —— 那么socket将是最重要的事情之一

我们将在本节课中做一些something cool，然后加入一些socket在其中。



CEO of Catbook：我们的Catbook很受欢迎，但是客户反映了一个重大问题，每次都得刷新才能看到新帖子，他们想要实时交互和CHAT！请做点什么！

so....

## Chatbook -- Catbook with Chat

我们最终的目标如下：

![image-20220401160428363](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204011604504.png)

注意，其中的Chatbook在App中的位置如下：

![image-20220401155731245](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204011557367.png)



## git checkout w8-starter

what should we do first？弄清我们需要的架构，如下：

![image-20220401162738009](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204011627144.png)



## 由于代码量比较大，需要的话直接复习视频即可。



## git checkout w8-step1



## git checkout w8-step2

创建数据库的Schema：

```javascript
const MessageSchema = new mongoose.Schema({
    // TODO (step 3.1): Write the schema for a message
    sender:{
        _if: String,
        name: String,
    },
    recipient:{
        _id: String,
        name:String,
    },
    timestamp: {type: Date, default: Date.now },
    content: String,
});
```

然后是API：

post

```javascript
// TODO (step 3.2): implement message route
router.post("/message", auth.ensureLoggedIn, (req, res) =>{
  console.log(`Received message from ${req.user.name} : ${req.body.content}`);

  const message = new Message({
    recipient: req.body.recipient,
    sender: {
      _id: req.user._id,
      name: req.user.name,
    },
    content: req.body.content,
  });
  message.save();
})
```

get

```javascript
router.get("/chat", (req, res) => {
  const query = { "recipient._id": "ALL_CHAT" };
  Message.find(query).then((messages) => res.send(messages));
});
```



## git checkout w8-step3

NewPostInput.js -- 调用post

```javascript
const NewMessage = (props) => {
  const sendMessage = (value) => {
    const body = { recipient: props.recipient, content: value };
    post("/api/message", body);
  };
```



## git checkout w8-step4

Chatbook.js -- 调用get

```javascript
const loadMessageHistory = (recipient) => {
  get("/api/chat", { recipient_id: recipient._id }).then((messages) => {
    setActiveChat({
      recipient: recipient,
      messages: messages,
    });
  });
};
```



**即使我们完成了以上的所有步骤，我们还是不能实时显示（刷新）我们的发言，必须得刷新才能看到。怎么解决？**



## Real time Chatbook with Socket.io

- Polling：Ask the server every (x) seconds -- 非常耗费资源，效率很低，相当于client不断地询问server（也就是不断的刷新）：有没有新消息？

![image-20220401191014705](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204011910901.png)

- ***we can teach the server to initiate！-- socket.io 原来之所以只能不断客户端问服务器 “有没有新信息？”的原因是：只能单向，服务器没法主动发消息给客户端，现在不一样了，有了socket，client和server之间可以建立一个通信，这样有新消息的时候，server直接将信息告诉client，client只需要这条新消息加到前端就行了，都不需要再次刷新（get）。***

![image-20220401191658843](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204011916134.png)

and then：

![image-20220401191716297](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204011917451.png)



## Let's Socket-ify Chatbook！—— git checkout w8-step5



## git checkout w8-complete

你将看到完成了socket部分的完整代码 -- 实际上只有三处，并且思路是：

- api.js中的post处加一个socket，一旦有post，server会直接把消息发送到各个client的前端，前端都不需要调用get，而是直接把新消息加到前端即可。

```javascript
router.post("/message", auth.ensureLoggedIn, (req, res) => {
  console.log(`Received a chat message from ${req.user.name}: ${req.body.content}`);

  // insert this message into the database
  const message = new Message({
    recipient: req.body.recipient,
    sender: {
      _id: req.user._id,
      name: req.user.name,
    },
    content: req.body.content,
  });
  message.save();
  socketManager.getIo().emit("message", message);//加上此行
});
```

-  Chat.js中加一个如下： **注意socket.off，因为不用的时候要关掉。否则后面又会新开一个socket，越积越多**

```javascript
useEffect(() => {
  socket.on("message", addMessages);
  return () => {
    socket.off("message", addMessages);
  };
}, []);
```

- Chat.js中加一个addMessage函数如下：

```javascript
const addMessages = (data) => {
  setActiveChat(prevActiveChat => ({
    recipient: prevActiveChat.recipient,
    messages: prevActiveChat.messages.concat(data),
  }));
};
```

















