# W0: HTML/CSS

构造一个完美的社交媒体，Catbook。

### 首先在你的编辑器（推荐VSCode，但我用IDEA）中打开拉取的catbook-react（这里面创建了很多分支，我们如果使用拉取他的仓库得来的，能一步一步跟着做，还是很不错的）



p.s. 如何把catbook拉取之后上传到自己的MIT-Lab仓库？把catbook拉取下来，放到你的仓库目录下，然后把文件中的.git删除，然后就当作自己的文件即可。

### 

- 第一个目标

![image-20220323102114043](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231021211.png)

- 分解这个第一个目标，首先是

![image-20220323102141795](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231021884.png)

- https://developer.mozilla.org/zh-CN/docs/Web/HTML（关于HTML的信息）

我尝试然后写出的结果如下：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Catbook</title>
</head>
<body>
    <h1>
        Miao Sun
    </h1>

    <hr />

    <div>
        <p>
            <strong>
                About Me
            </strong>
        </p>
        <p>
            I am more of a dog person but I'm just trying to fit in and get catbook
        </p>
        <p>
            <strong>
                My Favorite Type of Cat
            </strong>
        </p>
        <p>
            I actually like dogs
        </p>
    </div>
</body>
</html>
```

运行结果如下：

![image-20220323104404763](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231044819.png)

但是实际上正确的实现方法是：

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Catbook</title>
    </head>
    <body>
        <h1>
        Miao Sun
        </h1>
        <hr />

        <section>
            <h4>About Me</h4>
            <p>
                I am more of a dog person but I'm just trying to fit in and get catbook
            </p>
        </section>

        <section>
            <h4>My Favorite Type of Cat</h4>
            <p>
                I actually like dogs
            </p>
        </section>
</body>
</html>
```



## 到此，为了与主讲人统一步伐，我们在拉取的catbook-react中运行，来到主讲人安排好的第一步分支w0-step1

```bash
git checkout w0-step1
```



- 关于我们如何运行Prettier，将在后面介绍。



- 此时，我们可以进行下一步了，但是由于存在修改，我们无法直接``git checkout w0-step2`，会报错如下：

```bash
$ git checkout w0-step2
error: Your local changes to the following files would be overwritten by checkout:
        index.html
Please commit your changes or stash them before you switch branches.
Aborting
```

此时，我们可以

1）把我们的更新进行[commit](https://so.csdn.net/so/search?q=commit&spm=1001.2101.3001.7020)

2）先stash本地更新。

3）放弃本地的修改

```css
git reset --hard
```



## 我们选择放弃本地的修改，然后切换到w0-step2：

```bash
miaosun2@miaosun2 MINGW64 /d/repo/catbook-react (w0-step1)
$ git reset --hard
HEAD is now at 33772f1 deleted corgi image

miaosun2@miaosun2 MINGW64 /d/repo/catbook-react (w0-step2)
$ git checkout w0-step2
Switched to a new branch 'w0-step2'
branch 'w0-step2' set up to track 'origin/w0-step2'.
```

此时，我们已经完成了我们所需要的html部分，下面我们通过css对其进行stylish

为了完成这一步，我们首先需要在该目录下创建一个css文件，然后在html中加入链接css文件的代码

![image-20220323112004046](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231120113.png)

然后加入链接代码：(注意，是在html的<head>中加入)

```html
  <head>
    <title>Catbook</title>
<!--    下面就是我们要添加的css链接代码-->
    <link rel="stylesheet" href="styles.css">
  </head>

```



下面，让我们开始使用css，首先是将我们的名字居中。我们做出的修改如下：

![image-20220323112802981](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231128116.png)

然后我们刷新html，就可以看到名字Kevin Sun Chen文本已经居中了。

<img src="https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231130946.png" alt="image-20220323113038723" style="zoom:50%;" />



## 然后让我们进入w0-step3

下面一步是将我们所有的文本都居中，我的实现方案就是将section也居中就行，而不必对每个框都居中

```html
<!DOCTYPE html>
<html>

<head>
  <title>Catbook</title>
  <link rel="stylesheet" href="styles.css" />
</head>

<body>
  <img src="cat.jpeg" />
  <h1 class="u-textCenter">Kevin Sun Chen</h1>
  <hr />
  <section class="u-textCenter">
    <h4>About Me</h4>
    <p>
      I am more of a dog person but I'm just trying to fit in and get catbook
    </p>
  </section>
  <section class="u-textCenter">
    <h4>My Favorite Type of Cat</h4>
    <p>
      I actually like dogs
    </p>
  </section>
</body>

</html>
```

实现结果如下：

![image-20220323130007298](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231300542.png)



然后是实现其他位置，如左右，我的代码如下：

```css
/* Your Code Here! */

.u-textCenter {
  text-align: center;
}

.u-textLeft {
  text-align: left;
}

.u-textRight {
  text-align: right;
}
```



```html
<!DOCTYPE html>
<html>

<head>
  <title>Catbook</title>
  <link rel="stylesheet" href="styles.css" />
</head>

<body>
  <img src="cat.jpeg" />
  <h1 class="u-textCenter">Kevin Sun Chen</h1>
  <hr />
  <section class="u-textLeft">
    <h4>About Me</h4>
    <p>
      I am more of a dog person but I'm just trying to fit in and get catbook
    </p>
  </section>
  <section class="u-textRight">
    <h4>My Favorite Type of Cat</h4>
    <p>
      I actually like dogs
    </p>
  </section>
</body>

</html>
```

最终结果如下：

![image-20220323130107297](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231301503.png)



## 完成这一步之后，让我们来到w0-step4

让我们导入一些字体，fonts，获取字体的最佳来源应该是：https://fonts.google.com/

![image-20220323131058383](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231310532.png)

进入这个网站，然后选择你想要的字体（select this style），然后：

1）选择@import，然后copy其中的代码（如上图所示），并将其放入css文件的顶端

```css
/* Your Code Here! */

@import url('https://fonts.googleapis.com/css2?family=**Open+Sans:wght@300;500**&display=swap');

.u-textCenter {
  text-align: center;
}
```

然后copy下面的，将其放入css-body

![image-20220323131758890](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231317037.png)

```css
/* Your Code Here! */

@import url('https://fonts.googleapis.com/css2?family=**Open+Sans:wght@300;500**&display=swap');

.u-textCenter {
  text-align: center;
}

body{
  font-family: 'Open Sans', sans-serif;
}
 
```

接下来我们刷新html，可以看到下面的画面，我们页面的字体已经被修改了。

![image-20220323131826601](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231318809.png)



## 进入w0-step5，让我们开始构建一个NavBar（导航栏）

```html
<!DOCTYPE html>
<html>

<head>
<!--  我们在head下加入一个nav bar-->
  <title>Catbook</title>
  <link rel="stylesheet" href="styles.css" />
</head>

<body>
  <nav class="navContainer">
    <h1 class="navTitle">Catbook</h1>
  </nav>

  <img src="cat.jpeg" />
  <h1 class="u-textCenter">Kevin Sun Chen</h1>
  <hr />
  <section class="u-textCenter">
    <h4>About Me</h4>
    <p>
      I am more of a dog person but I'm just trying to fit in and get catbook
    </p>
  </section>
  <section class="u-textCenter">
    <h4>My Favorite Type of Cat</h4>
    <p>
      I actually like dogs
    </p>
  </section>
</body>

</html>
```

然后刷新页面，可以看到如下效果：

![image-20220323132343635](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231323928.png)

下一步是着色方案，我们知道twitter和Facebook之类的网站都有一个通用的配色方案，我们可以模仿这种行为。并尽可能多的重用颜色。

我们将css文件修改如下：

```css
/* Your Code Here! */

@import url("https://fonts.googleapis.com/css?family=Open+Sans:300,600");

:root{
  --primary:#396dff;
  --gray:#f7f7f7;
  --white:#fff;
}

body {
  font-family: "Open Sans", sans-serif;
}

.u-textCenter {
  text-align: center;
}

.navTitle{
  color: var(--primary)
}
```

然后刷新网页，可以得到：

![image-20220323133000274](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231330485.png)



此外，这种方案的强大之处在于，你可以点击来找寻你喜欢的颜色：

![image-20220323133101057](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231331271.png)



## 下面让我们切换到w0-step6

让我们将NavBar的背景换成蓝色，字体换成白色吧！

Hint：you may need a new container class!



实际上，我们加上如下信息即可

![image-20220323134357391](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231343451.png)

刷新html，如下：

![image-20220323134608765](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231346994.png)



## 让我们进入step7

需要注意的是：我们的网站存在一些void，如果你仔细观察，你会发现网站的边缘处仍是空白：

![image-20220323134912014](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231349110.png)

这是我们需要解决的问题，如何解决？



### inspect！

我们右键，然后检查inspect，然后就能看到如下：

![image-20220323135507804](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231355884.png)

我们鼠标悬停，最终可以找到，导致void边缘的原因是body的=margin = 8px，如下图所示：

![image-20220323140301335](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231403395.png)



在找办法解决这个问题之前，我们先了解一下html的模型，每个html中的框都有下面四个部分：

![image-20220323140450254](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231404335.png)



那么我们如何在我们的html和css代码中定位这部分（比如body的margin）并且消除他们呢？

很简单，和之前一样，在html中为你要操作的框创建一个类，然后操作，如下：

![image-20220323140706202](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231407278.png)

于是我们在css中将body修改为：

```css
/* Your Code Here! */

@import url("https://fonts.googleapis.com/css?family=Open+Sans:300,600");

:root {
  --primary: #396dff;
  --grey: #f7f7f7;
  --white: #fff;
}

body {
  font-family: "Open Sans", sans-serif;
  /*在css中修改margin值*/
  margin: 0;
}

.u-textCenter {
  text-align: center;
}

.navContainer {
  background-color: var(--primary);
}

.navTitle {
  color: var(--white);
  font-size: 20px;
  /* Below cancels out some of the default styling of h1 */
  margin: 0; 
  font-weight: normal;
}

```

然后刷新html，即可看到void消失。



### ordering

下一步，是了解css中的Ordering，比如当你设置一个margin值的时候，很明显，这个框的四周都会变成10px，那么如何实现四个方向上的不同margin呢？方案是通过ordering，比如对margin赋了四个值，这四个值是有默认顺序的，如下：

![image-20220323141237049](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231412163.png)



为了锻炼这部分能力，让我们为这个NavBar中的字母加上一个pedding，在进行这之前，我们就不得不提一个：

8pt Grid System

它会使你的界面看起来更整齐：

p.s. 注意，八点系统不是指间隔必须为8，而是间隔之间应该以8px为增量：

```css
--xs: 4px;
--s: 8px;
--m: 16px;
--l: 24px;
```

![image-20220323141540654](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231415773.png)



如此，我们的css的代码就变成了：

```css
/* Your Code Here! */

@import url("https://fonts.googleapis.com/css?family=Open+Sans:300,600");

:root {
  --primary: #396dff;
  --grey: #f7f7f7;
  --white: #fff;

  --xs: 4px;
  --s: 8px;
  --m: 16px;
  --l: 24px;
}

body {
  font-family: "Open Sans", sans-serif;
  /*在css中修改margin值*/
  margin: 0;
}

.u-textCenter {
  text-align: center;
}

.navContainer {
  /*在此处加入pedding，实现容器的pedding变化*/
  padding: var(--l) var(--m);
  background-color: var(--primary);
}

.navTitle {
  color: var(--white);
  font-size: 20px;
  /* Below cancels out some of the default styling of h1 */
  margin: 0; 
  font-weight: normal;
}
```



## step8

下面开始进行边界半径，同样的思路，先对图片加类名，然后在css中对其进行操作：

![image-20220323142921103](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231429164.png)

修改完之后，结果如下：

![image-20220323143206523](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231432716.png)



## 完成上面之后，下面进入step 9

But can you make it perfectly round?

我尝试了直接修改的borde-radius值，想使其无限逼近⚪，但是由于我们的猫猫图片不是正方形，所以当竖直方向上已经圆的时候，水平方向上就无法再增加圆周半径了。

```css
--max:600px;

img.avatar {
  max-width: 100%;
  border-radius: var(--max);
}
```

上面的代码效果如下图所示：

![image-20220323143810646](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231438812.png)



## 进入step 10

此时代码如下：

```html
<!DOCTYPE html>
<html>

<head>
  <title>Catbook</title>
  <link rel="stylesheet" href="styles.css" />
</head>

<body>
  <nav class="navContainer">
    <h1 class="navTitle">Catbook</h1>
  </nav>

  <div class="avatarContainer">
    <div class="avatar"></div>
  </div>
  <h1 class="u-textCenter">Kevin Sun Chen</h1>
  <hr />
  <section class="u-textCenter">
    <h4>About Me</h4>
    <p>
      I am more of a dog person but I'm just trying to fit in and get catbook
    </p>
  </section>
  <section class="u-textCenter">
    <h4>My Favorite Type of Cat</h4>
    <p>
      I actually like dogs
    </p>
  </section>
</body>

</html>
```

### and css：

```css
/* Your Code Here! */

@import url("https://fonts.googleapis.com/css?family=Open+Sans:300,600");

:root {
  --primary: #396dff;
  --grey: #f7f7f7;
  --white: #fff;

  --xs: 4px;
  --s: 8px;
  --m: 16px;
  --l: 24px;
}

body {
  margin: 0;
  font-family: "Open Sans", sans-serif;
}

.u-textCenter {
  text-align: center;
}

.navContainer {
  padding: var(--s) var(--m);
  background-color: var(--primary);
}

.navTitle {
  color: var(--white);
  font-size: 20px;
  /* Below cancels out some of the default styling of h1 */
  margin: 0; 
  font-weight: normal;
}

.avatarContainer {
  padding: 0 35%;
}

.avatar {
  /* make it responsive */
  max-width: 100%;
  width: 100%;
  height: auto;
  display: block;
  /* div height to be the same as width*/
  padding-top: 100%;

  /* make it a circle */
  border-radius: 50%;

  /* Add image */
  background-image: url("cat.jpeg");

  /* Centering on image`s center*/
  background-position-y: center;
  background-position-x: center;
  background-repeat: no-repeat;

  /* it makes the clue thing, takes smaller dimension to fill div */
  background-size: cover;

  /* it is optional, for making this div centered in parent*/
  margin: 0 auto;
}
```

此时，我们的界面已经非常接近了：

![](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231443972.png)

但是仍需要将下面的文本变成两列，在解决这个问题上，主讲人推荐的是flex而非float：

![image-20220323144638527](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231446708.png)

具体实现方案是：

将两个想要竖直两列的代码放入一个新的div（名字是u-flex）：

```html
<div class="u-flex">
  <section class="u-textCenter">
    <h4>About Me</h4>
    <p>
      I am more of a dog person but I'm just trying to fit in and get catbook
    </p>
  </section>
  
  <section class="u-textCenter">
    <h4>My Favorite Type of Cat</h4>
    <p>
      I actually like dogs
    </p>
  </section>
</div>
```

然后将css中对u-flex  —— div 为flex

```css
.u-flex{
  display: flex;
}
```

最终结果如下：

![image-20220323145329941](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231453096.png)



关于flex：

![image-20220323145423786](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231454911.png)



## step11

我修改后的代码如下
![image-20220323150334680](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231503838.png)

然后最终结果如下：

![image-20220323150554691](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231505835.png)



## step 13

后续作业：

https://docs.google.com/presentation/d/1pbhvdAKglYl8Uz7tEh-iXtlkWqiONeIiIjKGLdGvZlY/edit#slide=id.g6cde467d40_0_83











