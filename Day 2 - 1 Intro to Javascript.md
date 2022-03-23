#  Day 2 - 1 Intro to Javascript



Javascript是什么？it's how we take HTML+ CSS and make it interactive!它让你的网页可以与服务器交互，也就是让你可以和网页交互。

## Where can we run JavaScript code?

## ----- Ctrl + Shift + J -----

**1、The browser console** —— 直接在chrome中快捷键运行

​	**chrome: Ctrl + Shift + J (on Windows) / Cmd + Option + J (on Mac)** 

2、Tied to our HTML file (more on that later！) —— 也就是说在后台运行，然后附加到我们的HTML网页网站上。



五种基本类型

- Number
- String
- Boolean
- Null
- Undefined



p.s. JavaScript中，=== 和 !== 而不是 == !=，使用==则会得到错误的结果，在Javascript中，如果使用==，则会执行类型强制转换再判断，比如：

```javascript
2 === "2";//运行这条，得到false

2 == "2"//运行这条，得到true（因为执行了类型强制转换，所以会得到true）
```



let 定义变量 - 可被重复赋值

```javascript
let myBoolean = true;
let myNumber = 12;
let myString = "Hello World!"
```



const 定义变量 - 不可被再次赋值（常量）

```javascript
const answerToLife = 6.148;
```



***p.s. JavaScript中，变量用小驼峰sunMiao***



![image-20220323155808469](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231558565.png)

 

运行JavaScript，可以在chrome的console中运行：

![image-20220323160059086](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231600135.png)

```javascript
console.log("hello");
//输出为:hello
```



此外还有 alert() 函数，用来弹出通知，代码如下：

![image-20220323161714304](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231617386.png)

数组：

![image-20220323162830910](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231628955.png)

 Javascript中的 数组也能出入：（像栈）

![image-20220323163121250](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231631326.png)



Function 函数：

![image-20220323164959434](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231649512.png)

  函数参数中回调函数：

![image-20220323170430715](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231704792.png)

注意不要像下面红叉下代码那样：

![image-20220323170631714](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231706802.png)

像addTwo这样简单的代码，我们可以简化一下代码：

![image-20220323170912869](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231709984.png)



映射 - map()

![image-20220323171154270](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231711482.png)

过滤 - filter()

![image-20220323172141860](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231721950.png)

对象 Object：

![image-20220323172434589](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231724753.png)

访问对象：

![image-20220323172638106](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231726201.png)

像Java中，复制数组得一个一个复制，直接赋值复制得到的就是一个引用，而不是一个真的copy。但是在Javascript中，我们可以通过 { } 这个拓展运算符来实现复制，如下：

![image-20220323174257678](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231742905.png)



类 classes

![image-20220323174808503](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231748797.png)

通过this访问类中元素，来写函数

![image-20220323174952642](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231749732.png)















