# Day 3 - 03 React Part 2

 为什么React要使用“组件包含组件”的思想？

1）让代码易读

2）每个组件有自己的功能

3）控制各个组件之间的信息流 —— 如果都写在一个文件中，那么代码的所有部分都是可以互相访问信息的了。



## State & Props

注意！不要在一个组件中直接编辑另外一个组建的状态State！那么我们该如何父子组件之间的状态改变？答案如下：   

![image-20220325111013287](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251110410.png)

## 关于Props

......





## 关于State

### State初始化：

![image-20220325113122177](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251131302.png)

 ### State的修改

有人可能觉得应该是：（但是这样是错误的（不通过set函数的话，可能会导致延后才检测到state的变化），我们应该通过set函数实现）

![image-20220325113054293](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251130373.png)

通过set函数实现：

如果我们不只是修改从false到true，我们还得注意如何进行增加，如下是一种实现方式：

![image-20220325113344542](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251133623.png)

但是更常用的方法是：

![image-20220325113436755](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251134070.png)

下面的代码执行会得到什么？

![image-20220325130803257](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251308371.png)

答案是：无法保证，**因为setState是异步的**，如果你想更新一个状态变量，然后再使用它，那么我们需要为此做一个特殊的解决方法。



## ......这个解决办法有点复杂，但是代码是简洁的，如下：

![image-20220325131609009](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251316120.png)

这个代码`useEffect`部分的作用，就是当person改变的时候，控制台输出person。保证我们能一直拿到最新的person值。



useEffect()有三种常见用法：（我们上面的属于第一种用法）

![image-20220325132023348](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251320464.png)



## get() 

用上前面我们介绍的方法，那么此时get就是：（可以看到，这个useEffect方法，首先在后端get到/api/packages的数据，然后将数据传递并且显示（setPackages）在前端。

![image-20220325132316928](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251323050.png)



## post()

下面是一个post()方法（改变一个用户的权限从admin变成非admin）：那么流程就是，首先将后端的/api/user/admin从admin改为！admin，然后在前段将admin改为！admin

![image-20220325132544667](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251325826.png)



 p.s. 注意，我们上面可以看到，对后端的操作，始终是要先于前端的，目的就是防止我们万一对后端的操作失败了，却由于把前端写在前面，最终导致后端没改，前端改了，前后不一致了。



## Example：Display a loading indicator

很多网页在我们等待的时候会先显示loading，然后加载完毕的时候，再显示从后端拿到的数据。那么他的实现如下：（通过一个condition ? resultTrue : resultFalse 来实现。

![image-20220325133608638](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251336737.png)



**当然，上面的代码也有一种更简洁的写法，如下代码**

![image-20220325133822554](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251338647.png)

**实际上也就是运用了JavaScript的特性，允许在html中用{}构造一个环境显示JavaScript变量（let content） —— 此外，我们还需要注意，这里的代码实际上是在一个JavaScript文件中，那么也就是通过一个（）在JavaScript中开辟了一个html环境。**

**总而言之，就是：这是一个Javascript代码，然后里面用（）开辟了一个html环境，然后html中，又用{}开辟了一个JavaScript环境，放入在最外层创建的JavaScript变量（但是是html语句 => let content = <html...><....>）**



此外，还有一种更简单的写法，如下：

![image-20220325134437443](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251344572.png)



## Loop rendering（循环渲染）

想显示在前端，必须有html，但是我们的数据如果是在JavaScript中，我们只能通过map函数，将JavaScript映射成html代码，然后再显示。  

![image-20220325134911501](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251349624.png)

具体实现如下代码：

![image-20220325135444970](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251354210.png)



## Math

- Math.abs()
- Math.min()、Math.max()
- Math.PI()、Math.sin()
- etc.



## Dates

![image-20220325135852127](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251358230.png)



## JavaScript的数据结构

set —— 同java



## Json

能够：

- 将对象转化为字符串（比如为了存储到database中）
- 将字符串再重新转成对象

![image-20220325140052691](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251400814.png)

















