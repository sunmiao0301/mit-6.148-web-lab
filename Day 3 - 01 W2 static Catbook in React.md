# Day 3 - W2: static Catbook in React

Recap: Writing Components

- We divide our app into components, and put one in each file
- Each component is a function with props as the input, and returns HTML-like code
- **( )** allows us to enter an HTML environment
- Inside the HTML environment, **{}** allows us to create a mini JS environment



## Workshop 2: Catbook in React

让我们通过下面一系列的图来理解React的思想：组件中的组件，直到某一层的组件已经很小，小到可以轻易实现；

### 第一层：

![image-20220324144503488](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241445623.png)

### 第二层：

![image-20220324144535349](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241445458.png)

### 第三层：

![image-20220324144606709](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241446879.png)



### 接下是props和state的实现：

![image-20220324144902203](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241449324.png)



![image-20220324144924084](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241449181.png)



props沿着树流淌，而state内置于各个组件之中。

![image-20220324145346350](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241453502.png)



## 以Instagram为例，我们看看它的代码结构是怎么样的：

![image-20220324145550543](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241455648.png)

更细一层：

![image-20220324145626668](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241456767.png)

然后到了最底层！（就得开始写html了）

![image-20220324151048270](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241510378.png)

具体例子如下：

![image-20220324151113897](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241511011.png)

然后在加上一个like功能：

![image-20220324151224889](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241512997.png)



我们暂时不做那么复杂的，我们的目标如下：

![image-20220324154943491](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241549594.png)

并且你可以看到，这里有一个Cat Happiness，如果你点击这条狗（猫？），它的幸福感就会增加。

## $ git checkout w2-starter

## $ npm install （注意安装npm）——  npm(Node.js Package Manager)是一个Node.js的包管理工具，用来解决Node.js代码部署问题

但是安装的时候会报错如下：

```bash
npm ERR! network
npm ERR! network If you are behind a proxy, please make sure that the
npm ERR! network 'proxy' config is set properly.  See: 'npm help config'

npm ERR! A complete log of this run can be found in:
npm ERR!     C:\Users\miaosun2\AppData\Local\npm-cache\_logs\2022-03-24T08_09_39_324Z-debug-0.log
```

我的解决方案是：

```bash
npm install -d
```

安装信息是：

```bash
miaosun2@miaosun2 MINGW64 /d/repo/catbook-react (w2-starter)
$ npm install -d
npm info using npm@8.3.1
npm info using node@v16.14.0
...
```

但是到了最后还是有问题，还是会报错如

```bash
npm ERR! code ECONNRESET
npm ERR! syscall read
npm ERR! errno ECONNRESET
npm ERR! network request to https://registry.npmjs.org/react-hot-loader/
-/react-hot-loader-4.13.0.tgz failed, reason: read ECONNRESET
npm ERR! network This is a problem related to network connectivity.     
npm ERR! network In most cases you are behind a proxy or have bad networ
k settings.
npm ERR! network
npm ERR! network If you are behind a proxy, please make sure that the   
npm ERR! network 'proxy' config is set properly.  See: 'npm help config'
npm timing npm Completed in 97711ms

npm ERR! A complete log of this run can be found in:
npm ERR!     C:\Users\miaosun2\AppData\Local\npm-cache\_logs\2022-03-24T
08_22_10_487Z-debug-0.log
```

我的解决方案是设置代理：

```bash
# 我的代理信息是：
https_proxy=http://127.0.0.1:33210 
http_proxy=http://127.0.0.1:33210 
all_proxy=socks5://127.0.0.1:33211

# 那么对应的解决方案就是：
npm config set proxy http://<proxy.company.com>:
npm config set https-proxy http://<proxy.company.com>

# 在命令行中也就是：
miaosun2@miaosun2 MINGW64 /d/repo/catbook-react (w2-starter)
$ npm config set proxy http://127.0.0.1:33210

miaosun2@miaosun2 MINGW64 /d/repo/catbook-react (w2-starter)
$ npm config set https-proxy http://127.0.0.1:33210
```

如此，则最终安装成功如下：

```bash
Run `npm audit` for details.
npm timing command:install Completed in 82874ms
npm timing npm Completed in 83351ms
npm info ok
```



## 解决之后，我们就可以开始ReactJS编码了

我们回顾一下我们的目标：

![image-20220324154943491](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241549594.png)

我们首先尝试制作一个组件树，那么在这个组件树中，应该有下面这些组件：

![image-20220324184901628](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241849000.png)

然后是在终端进行，首先让我们在idea中同时展示两个终端，如下操作即可：

![image-20220324185428969](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241854081.png)

然后在其中一个终端中运行：

```bash
miaosun2@miaosun2 MINGW64 /d/repo/catbook-react (w2-starter)
$ npm run hotloader

> catbook-react@1.0.0 hotloader
> webpack serve --config ./webpack.config.js --mode development --port 5000

<w> [webpack-dev-server] "hot: true" automatically applies HMR plugin, you 
don't have to add it manually to your webpack configuration.
<i> [webpack-dev-server] [HPM] Proxy created: /api  -> http://localhost:300
0
<i> [webpack-dev-server] [HPM] Proxy created: /socket.io  -> http://localho
st:3000
<i> [webpack-dev-server] Project is running at:
<i> [webpack-dev-server] Loopback: http://localhost:5000/
webpack 5.11.1 compiled successfully in 8383 ms
assets by status 1.87 MiB [cached] 1 asset
cached modules 1.47 MiB (javascript) 24.9 KiB (runtime) [cached] 375 module
s
webpack 5.11.1 compiled successfully in 69 ms
```



***hotloader —— 热加载：Navigate to localhost:5000 and see the page update with your live changes !***

之所以开两个终端，就是为了保持热加载器始终在一个终端中处于开启状态。



我们可以访问一下localhost:5000

![image-20220324190459743](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241904834.png)



我们可以打开对应都代码，看一下组件，其中App是由NavBar和Profile构成的，让我们看一下Profile:

![image-20220324191536153](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241915348.png)

可以看到，在上面的代码中，其中的ClassName类名都是以Profile开头的，但是这不是必须的，只是为了我们在对应的CSS中，知道每个部分的来源。



主讲人要求先实现NavBar，我自己实现如下：

css文件：

```css
/** 
 * T-ODO Step 0:
 * Implement Navbar.css using the old_styles.css file
 * Remember: styles in React use the component in their style name (ex: .navContainer --> .NavBar-container)
 * .<old style> --> .<Component>-<style-name>
 * 
 */
.NavBar-backGround {
    background-color: var(--primary);
}

.NavBar-text {
    font-size: 40px;
    color: white;
}
```

JavaScript文件：

```javascript
import React from "react";

import "./NavBar.css";

/**
 * The navigation bar at the top of all pages. Takes no props.
 */
const NavBar = () => {
  return (
    // // T-ODO Step 0: Implement NavBar similar to old navigation bar found in old_index.html.
    // // Hint: Look for the <nav> HTML tag.
    // // Remember "class" attributes in HTML are renamed to "className" in ReactJS.
    // null
      <div className="NavBar-backGround">
        <h1 className="NavBar-text">Catbook</h1>
      </div>
  );
};

export default NavBar;
```

但是实现的结果并不怎么好，边框还是白色的，应该是html的某层框没解决，如下所示：

![image-20220324193715787](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241937905.png)

实际上，我们将css改为如下所示，即可解决问题：

```css
.NavBar-backGround {
    background-color: var(--primary);
    padding: 40px 40px 40px 40px;
}

.NavBar-text {
    font-size: 50px;
    color: white;
}
```



## $ git checkout w2-step1

下面我们要做的就是点击图标，然后增加幸福感，这个功能看似很简单，实际上是cookie clicker的全部内容。（cookie cliker，一个影响数百万人的大型游戏，如下）

![image-20220324195518230](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241955481.png)

我们要做的是将state存储下来，然后作为props传递给组件。下面的图就是我们要做的全部内容：

![image-20220324195836844](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203241958948.png)



## git checkout w2-step2

在step2中，我们完成了Cat Happiness组件的添加，以及数字的显示，但是还没有完成点击猫猫，数字增加的功能



## git checkout w2-complete

在complete中，我们完成了增加幸福感的功能。



## Recap

![image-20220324202239030](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203242022309.png)

and

![image-20220324202258209](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203242022333.png)



## 如果还没有看懂，强烈建议回顾一下幻灯片，幻灯片的质量非常之高！



看了幻灯片，我想自己写下功能，点击加1：

首先是：



我们要知道要做什么，点击图片，然后底下的数字加1，那么具体实现是怎么样的？

1、首先得给图片一个函数，让他被点击的时候，调用一个函数，如下：

```javascript
<div className="Profile-avatarContainer" onClick={incrementCatHappiness}>
```

可以看到，这个被调用的函数叫做 incrementCatHappiness



2、此外，这个增加的框子也在profile控件内，所以我们应该给它一个状态值，相关操作是：

```javascript
import React, { useState } from "react";

...

  const [catHappiness, setCatHappiness] = useState(0);

  const incrementCatHappiness = () => {
    setCatHappiness(catHappiness + 1);
  };
```

可以看到，这个状态值是`const [catHappiness, setCatHappiness] = useState(0);`，那么我们该如何控制

3、此外，我们应该将catHappiness这个props值传递给控件来显示，如下：

```javascript
        <div className="Profile-subContainer u-textCenter">
          <h4 className="Profile-subTitle">Cat Happiness</h4>
          <CatHappiness catHappiness={catHappiness} />
        </div>
```













