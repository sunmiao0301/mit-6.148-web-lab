# Day 6 - 02 Accounts and Authorization

这节课程不会教你去实现，但是会告诉你身份验证背后的原理。对于一个网站，一般是username + password。

**需要注意的是，有些网站不需要你每次都重新登录，在一段时间内，他允许你直接登录（在你第一次已经通过账号密码登陆过一次的情况下），怎么实现的？**

是通过下面两个东西

![image-20220401135501868](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204011355078.png)



## SESSION

![image-20220401140011157](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204011400404.png)

注意，session 是被存储在server上的。



## JSON web Token

原理和session差不多，区别在于被加密。过程如下：

- 用户HTTP提交登录信息（账号密码）
- 服务器创建一个JWT -- JSON Web Token（JWT是一个加密的信息块，存储了你提交的登录信息）
- 你的客户端前端将JWT存储在本地存储中。
- 未来再需要登陆的时候，直接借助JWT即可



## 身份验证背后的细节

密码怎么存？

- 密码存储在数据库中？ BAD！密码未加密，黑客轻松阅读！
- 对密码加密之后再存入数据库 -- Password Hash Salting 

![image-20220401141450460](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204011414580.png)



## Google Auth Server

但是在weblab中，我们将不去实现这个，而是**using a registration system they already use and trust -- their Google account**

![image-20220401142636147](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204011426283.png)



## 代码部分

从17:04开始

 







