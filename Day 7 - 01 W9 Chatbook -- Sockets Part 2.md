# Day 7 - 01 W9: Chatbook -- Sockets Part 2

- socket是让你能够从server向client发起交流，而不仅仅是从client向server单向发起的工具。

## Need more - from part1 to part2

在Sockets Part 1 中，我们完成了socket，但是那个只允许我们广播，也就是一个人发帖，大家都能看到，但是如果你想要发私信给某个人的话，我们就需要更多！

## 解决方案

比如在下面这张图中，Fluffy想要只发送私聊信息给Whiskers，问题在于：服务器不知道哪个是Whiskers的socket，所以无法直接把消息发到那个socket

![image-20220404175420496](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204041754653.png)

但是服务器可以问，谁是Whiskers？然后Whiskers回答我是！然后服务器通过req.user来验证一下，就可以了

![image-20220404175659731](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204041756883.png)



## 实操

![image-20220406141937584](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204061419980.png)





