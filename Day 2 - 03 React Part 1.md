# Day 2 - 2 React Part 1

 在此之前，让我们回顾一下HTML CSS JavaScript

![image-20220324102812411](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241028732.png)



如果你分析如何用HTML、CSS以及JavaScript去构建一个Facebook，你可能会发现你需要做大量重复的工作，比如多个post，多个friend等等，但是如果你选择React，React允许我们重用我们称之为组件的东西 —— 更有效率、编码快、易阅读、助于调试等等。

![image-20220324103717959](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241037081.png)

下面是React的架构：

![image-20220324103823155](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241038299.png)

Navbar Sidebar Feed

![image-20220324103833300](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241038450.png)

让我们分解它，分析它，那么实际上是构成了一个组件树结构

![image-20220324103958317](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241039416.png)

## 对React的总结

综上所述，我们可以知道，React是一个框架，并且让你能够分解你的网站为多个组件。你的网站（app）也就被分解成了一种组件构成的树结构。



每个组件又可以被分析，以评论为例：

![image-20220324104500211](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241045312.png)

我们可以看到评论组件由：加粗的名字、评论内容、一些Like、Reply选项，时间，构成。



但是虽然组件是可重用的，但并不意味着评论内容也是可重用的，不同的评论块的框架是一样的，但是内容却不一样，比如名字和评论内容等。

针对这个问题，React的解决方法是：使评论块的框架成为一个Parent，然后传递**Props**给child组件：

### Props是输入

![image-20220324104953119](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241049211.png)

但是需要注意：

### Props是不可变的，也就是说，当我们传递一个Props的时候，他将不再改变

但是评论组件还有like等选项，每当有人点击like，like值都会增加，所以我们应该考虑这一点（不能用Props实现），那么React为我们提供了一个可变的 —— **State**，如下所示：

![image-20220324105736344](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241057482.png)

 

## 多说无益，开始编码

让我们模仿一个Facebook的界面（使用React）：

分析一下下面左边的界面，并将其整理为树，将是右边的情况：

![image-20220324110211364](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241102657.png)

...

![image-20220324111317142](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241113262.png)



## 下面，让我们实际运用起来React吧 —— 编写Facebook

可以看到，一个Facebook界面是由很多组件如NavBar、Post、Photos等构成的，每个NavBar这样的组件又是由很多更小的组件构成，总而言之，这就是React思想的重点 —— 这样使得代码看起来更简单。

![image-20220324111621534](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241116684.png)



下面开始讲解React编码：首先在JavaScript中导入React以及我们需要用的组件，然后我们有一个App主函数，App中使用div分割我们导入的组件，如下：（这个框架看起来很简单，实际上也是Facebook所需要的所有代码，但是虽然这样看起来很简单，但是每个小组件（如NavBar等）具体如何实现才是最重要的。

![image-20220324111956736](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241119882.png)



## 首先是Props：

![image-20220324112405133](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241124334.png)

那么代码中，具体该如何传递Props呢？见下面：

![image-20220324112628029](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241126149.png)

这是App.js中展现，更加细化的情况下，我们还需要对Intro.js进行编码：

Intro.js仍旧是一个JavaScript文件，并且内容也是一个函数，并且他只返回html代码：

![image-20220324113111141](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241131248.png)

但是仔细分析上面的Intro.js代码，我们可以发现这是一个被限制死的Intro，Lives in和Pronunciation都是写好的字段，如果这样的话，我们是没法重用这些小组件的，如何解决？

## 答案是Props，以Intro.js为例，实现如下：

![image-20220324131402751](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241314882.png)

可以看出，props看起来像一个对象，有着city、pronunciation等属性

此外，需要注意的是，我们使用了花括号，{ }，在html中使用花括号的含义是：在html环境中创建了一个JavaScript环境。



## 继续以Photo为例，实现如下：

![image-20220324133830573](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241338710.png)

然后同理，要使得图片是可变的，我们还是借助于props:

![image-20220324133900132](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241339260.png)



## 接下来是Post.js

首先是特定的情况：

![image-20220324141134000](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241411096.png)



然后是基于props的情况：

![image-20220324140854356](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241408498.png)

但是可以看到，我们还没有解决  点击like，like数量加1的情况，实现方案如下：（我们用到了state来解决这问题）

![image-20220324141447672](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241414849.png)



需要注意的是：CSS中用的是Class，React用但是ClassName



p.s. 有哪些公司使用React？

![image-20220324142247621](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241422756.png)

##  It is nonsense today but when you begin to code tomorrow, everything will be meaningful. 













