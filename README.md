# MIT-6.148-Web-Lab

## about web.lab

learn how to build a dynamic, server-backed website.

## what is web.lab

A 6-Unit MIT IAP Class which teaches the fundamentals of web development.

## class structure

we walk through the basics of web development: how to program in **HTML**, **CSS**, and **JavaScript**, how to **launch a backend server using node.js**, and how to **integrate a database into your web-app using MongoDB**. In the second week, we teach **more advanced topics and sponsors** give cool lectures on how students can utilize industry techniques and technoligies in their project.

## schedule

https://weblab.mit.edu/schedule/

Week 1 - we build an app from scratch together!

Week 2 - advanced topics + sponsor lectures

Week 3 - code, code, code 

Week 4 - Code, Code, Code

## How 

先看课，并做md笔记，后看ppt，未来复习的时候看ppt就行（ppt做的很好，看ppt就能回忆起来）

## Tips

课程是推荐使用VSCode（或是其他你熟悉的编辑器）进行，我选择的是IDEA，但是使用过程中，会出现一些问题，比如在W1中，当我`git checkout`到其他分支之后，js文件将会变得无法编辑，成为read-only文件，解决方案是：Close Project，然后删除项目文件目录下的.idea文件即可，重新打开catbook-react项目即可。

## resources

https://weblab.mit.edu/resources/

| Day d - p                                  | Doc link                                                     | Video link                                                | Description                                                  |
| ------------------------------------------ | ------------------------------------------------------------ | --------------------------------------------------------- | ------------------------------------------------------------ |
|                                            |                                                              |                                                           |                                                              |
| Day 1 - 01 Kick Off                        | [doc link](https://docs.google.com/presentation/d/1l67OznkGj_sopRDzieZOH6eq1zOu5iNqMO4hAOEf0sQ/edit#slide=id.g4c281c9bc6_0_19) | [video link](https://www.youtube.com/watch?v=fg64qyD3yEc) | 开课啦！                                                     |
| Day 1 - 02 Intro to Git/Github             | [doc link](https://docs.google.com/presentation/d/1FY2B6fZPowYPdQLUUYBtJW12SIVQzMaL5u-PSEG3nKI/edit) | [video link](https://www.youtube.com/watch?v=fg64qyD3yEc) | 合并冲突<br>Alice和Ben同时拉取了代码，然后ben修改了代码的第四行并先于Alice push到了main上，然后Alice也修改了第四行，那么此时Alice也想push就是不行的，Alice必须用pull拉取ben更新的main，并且发生冲突，此时git server会提醒你进行手动合并。合并之后，Alice再push就行了。 |
| Day 1 - 03 Intro to HTML/CSS               | [doc link](https://docs.google.com/presentation/d/1pbhvdAKglYl8Uz7tEh-iXtlkWqiONeIiIjKGLdGvZlY/edit#slide=id.g10b6d7f4a9a_0_0) | [video link                                               | HTML is…a bunch of boxes, nested inside of each other.<br><br/>学习Web，推荐网站MDN而不是W3SCHOOLS<br><br/>为什么不只用`<div>`呢？因为div不包含语义，就是个标签，我们应该针对不同的情况选择不同的tag，来保证HTML代码的可读性，比如一些包含语义的tag如`<section><article><nav><header><footer>`等<br/><br/>CSS - 通过给tag一个类class，然后在css中对类class给描述。<br/>![image-20220325142944624](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251429792.png)<br><br><br/>综上，不难想到有一种思路是：全部用div构建你的网页的html，然后创建很多css的class类型，最后将class应用于div中 |
| Day 1 - 04 W0: HTML/CSS                    | [doc link](https://docs.google.com/presentation/d/1pbhvdAKglYl8Uz7tEh-iXtlkWqiONeIiIjKGLdGvZlY/edit#slide=id.g10b6d7f4a9a_0_0) | [video link](https://www.youtube.com/watch?v=WzSKqhhZxmY) | 命令行做一个catbook静态网页<br><br/>html中通过`<link rel="stylesheet" href="style.css" />`来完成html和css的链接<br/><br/>导入字体<br/><br/>做出来的catbbok边缘有void，怎么解决?点击inspect -> 左上角的光标，然后就能看页面上各个部分对应的代码，通过代码，我们可以发现这关系到HTML Box Model<br/>![image-20220325151407622](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251514687.png)<br/><br/>ordering -> 上右下左（顺时针）<br/><br/>8 grid system<br/><br/>flex (not float) -> Flexbox is a flexible box that lets you control the direction, sizing, distribution, and more of items.使用方法如下：<br>![image-20220325152400093](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251524193.png)<br/><br/>![image-20220325152428462](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251524552.png) |
| Homework 1                                 |                                                              |                                                           |                                                              |
|                                            |                                                              |                                                           |                                                              |
| Day 2 - 01 Intro to JavaScript             | [doc link](https://docs.google.com/presentation/d/1HxK7RegAF0hPNnUhICKAxw42pMGzDY0FF0MVairnPGc/edit#slide=id.g10a6c294d5e_0_0) | [video link](https://www.youtube.com/watch?v=o4brcBVCzsw) | JavaScript，让静态页面变得可交互，成为动态页面。<br/><br/>在哪运行JavaScript代码？1）chrome -> Ctrl+Shift+J -> Console  2）在HTML代码中与运行JavaScript代码！<br/><br/>JavaScript五种基本类型：Boolean、Number、String、Null、Undefined<br/><br/>定义变量用let、定义常量用const、命名规范小驼峰、不要使用var（忘记JavaScript中var的存在）、console.log()用于输出、alert()用于弹窗输出<br/><br/>JavaScript数组初始化：`let pets = ["cat", "dog", "pig", "bird"];`<br/>JavaScript数组从尾部“出栈”：`pets.pop();`<br/>JavaScript数组从尾部“入栈”：`pets.push("rabbit");`<br/><br/>JavaScript函数：<br/>`const function = (parameter1, parameter2, ...) => {`<br/>`const ret = parameter1 + 1;`<br/>`return ret;`<br/>`}`<br/><br/>如果想要在JavaScript函数内调用其他函数，则需要回调函数Callback：<br/>![image-20220325154007231](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251540306.png)<br/><br/>对于上面的情况，由于回调函数足够简单，所以我们也可以进行简化：<br/>![image-20220325154127510](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251541581.png)<br/><br/>此外，数组还有一些内置的非静态函数：map()，filter()<br/><br/>JavaScript中的对象Objects<br><br>JavaScript总结如下<br>![](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251546081.png) |
| **Day 2 - 02 W1: JavaScript**              | [doc link](https://docs.google.com/presentation/d/1HxK7RegAF0hPNnUhICKAxw42pMGzDY0FF0MVairnPGc/edit#slide=id.g10a6c294d5e_0_0) | [video link](https://www.youtube.com/watch?v=1a_C-ZVMtGE) | **贪吃蛇 —— 需要JavaScript的时候可以复习这个W1**             |
| Day 2 - 03 React Part 1                    | [doc link](https://docs.google.com/presentation/d/1wr58fv2XNTNlEbmbgedOlianOKCRc3I2hlxV4HDNwcg/edit#slide=id.p) | [video link](https://www.youtube.com/watch?v=E0uvuti9lfk) | React是由Facebook开源的一个进行创建用户界面的一款JavaScript库。用React搭建的App属于组件构成的组件。一路拆分下去，可以形成一个组件树结构，其中的各个组件是可复用的。<br/><br/>Props：Inputs passed from a parent to a child component.<br/>State：Private information maintained by a component.<br><br>下面是关于Props和State的使用的一个例子：<br/>![image-20220325161310593](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251613665.png)<br/><br/>Each component is a function with props as the input, and returns HTML-like code<br/>**( )** allows us to enter an HTML environmentInside the HTML environment <br/>**{}** allows us to create a mini JS environment<br/><br/>注意！React使用className而不是class，所以你的ReactJS中()构造的HTML环境内的HTML代码得用className而不是class，才能使得HTML被CSS修饰。 |
|                                            |                                                              |                                                           |                                                              |
| **Day 3 - 01 W2: static Catbook in React** | [doc link](https://docs.google.com/presentation/d/1FY7ACT58YIP4OAMstNkilDLC3xKYfrWTE-RngCosHYA/edit) | [video link](https://www.youtube.com/watch?v=c18sTH8wztw) | **点击加1（cookie clicker的本质！）—— 需要ReactJS下的Props和State操作的时候可以复习这个W2**<br/><br/>其实就是怎么在ReactJS中解决Profile组件和CatHappiness组件之间Props和State的传递问题。 |
| Day 3 - 02 Backend and APIs                | [doc link](https://docs.google.com/presentation/d/1UhDM9EXqgfuboCO6u4A_akB_wsSynb7Apc3WdXwIbmk/edit#slide=id.p) | [video link](https://www.youtube.com/watch?v=zIA3U9QtRmg) | HTTP / HTTPS、HTTP Methods、Request、Response、Status Codes<br/><br/>状态码是隐藏的：chrome -> Ctrl+Shift+J -> Network，然后进行网页上的操作（比如刷新）就能看到状态码<br/><br/>APIs = Application Program Interface<br/><br/>可视化API -> Swagger |
| Day 3 - 03 React Part 2                    | [doc link](https://docs.google.com/presentation/d/14ha-xSK3iKGwTyb_HwG1CbaffDjGw_EjDWwH7eiZpmg/edit#slide=id.gb2bbafee77_0_50) | [video link](https://www.youtube.com/watch?v=MwlXn_6ymzU) | You can’t directly edit a component’s **State** from another component!<br>对应的解决办法是：Callback Functions<br><br/>让State不动，让Props传递。<br><br>State的修改（set）是异步的，我们需要借助useEffect方法解决异步带来的影响。<br/><br/>get() and post()<br/><br/>JSX<br/>![image-20220325165034265](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251650644.png)<br/><br/>loading功能实现的三种方法<br><br/>map()内置函数在React中的运用（转JavaScript中的数据为HTML代码，便于前端)<br/><br/>JSON：Convert objects into strings and vice versa!<br>Useful if you need to store info as a string (eg. in a database) and then retrieve it later<br/>Our utilities.js get/post request code does this |
|                                            |                                                              |                                                           |                                                              |
| **Day 4 - 01 W3: Build Feed Skeleton**     | [doc link](https://docs.google.com/presentation/d/1qTJOPjyIx__AeFHDgmpLvBk2fj9dEQluAl35nDFHZ1Q/edit#slide=id.gab8bae0ff4_1_6) | [video link](https://www.youtube.com/watch?v=CElrdn1Ix-s) | **建议直接`git checkout w3-step10`看代码（这女的讲的像shit）—— 需要More React, Using APIs, and Routing的时候可以看W3** |
| Day 4 - 02 How to Wireframe                | [doc link](https://docs.google.com/presentation/d/16oWnI0ptuhoHom1l56aVSE2ME4XvbpdrU4TpsysG6TM/edit#slide=id.p) | [video link](https://www.youtube.com/watch?v=L2jU9Fz8Zbw) | 本节课有Review<br>![image-20220327184323186](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203271843341.png)<br><br/>回顾了一下W4的组件结构以及设计思路<br><br>Design and Wireframing<br>- **figma !!!**<br>- google slides<br/>- any wireframe software / Photoshop / Sketch / etc. |
| Day 4 - 03 NodeJS & Setting Up the Server  | [doc link](https://docs.google.com/presentation/d/1n4LuT6Lx1PyA_eLtZzL65rQc7Shoq3U6Sj5DVTyG3j8/edit#slide=id.g6d2ca994e4_1_11) | [video link](https://www.youtube.com/watch?v=lqG_b2g9mzQ) | server绑定在某个计算机的一个端口上，protocol://domain:port，其中protocol往往是http和https，domain是域，port是端口，你自己的计算机有一个特殊的域：localhost<br><br/>Node.js：我们之前往往是在chrome浏览器的console中运行Javascript，NodeJs allows users to run JavaScript code outside of the browser on the local machine<br/><br/>npm：Node Package Manager，后端调试主要命令`npm run hotloader`<br/><br/>我们执行`npm install`的时候，实际上是下载了一些json文件和一个node_modules文件夹，其中，json文件holds project metadata（每个Javascript项目有一些必需信息），而node_modules文件夹下则是包含了一些依赖（我们在项目中直接使用的外部代码）<br/><br/>Creating our first API endpoint：<br>app.get("/api/test", (req, res) => {<br/>    res.send({ message: "Wow I made my first API!"});<br/>});<br/><br/>Adding Error (server cause) Handing<br/><br/>写API代码的时候需要注意，当服务器收到请求的时候，它会从你代码中写的第一个API endpoint按顺序从上而下匹配，所以顺序很重要！<br/><br/>在Node.js中，localhost:5000 → **hotloader, processes react code, to view your website**<br>localhost:3000 → **node server**, **our backend server, to view your backend**<br/><br/>Middleware |
| **Day 4 - 04 W5: Building your own API**   | [doc link](https://docs.google.com/presentation/d/12TE9u0nDS9cyKcahg0pt_AFxRvD-FfjmGuuIsAWZj8Y/edit#slide=id.p) | [video link](https://www.youtube.com/watch?v=1hQSr2jZsN4) | **为catbook编写getStory、postStory、getComment、postComment四个API—— 需要编写API的时候可以复习这个W5**<br/><br><br>代码解耦，一般将api单独写入一个api.js，并通过router将其链接到主app.js。<br/><br/>我们编写api的时候，用到(req, res)，req is the incoming request，res is your server's response，如果是get，我们就用req.query，如果是post，我们就用req.body。<br><br/>GET-Comment：![image-20220401125929823](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204011259980.png)<br/>POST-Comment：![image-20220401130058488](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204011300579.png) |
|                                            |                                                              |                                                           |                                                              |
| Day 5 - 01 Review                          | [doc link](https://docs.google.com/presentation/d/1diTCJGqnk4Alz8jlFMA5q3qiieexM17F-dKaIx05o5s/edit#slide=id.p) | [video link](https://www.youtube.com/watch?v=zY8Kh9G64fA) | Server is another computer and you can get data from it. File access, Centralization and Security is the need for a server.<br><br>HTTP是一种协议，是客户端和服务器之间通信的方法。<br/><br/>JavaScript是异步语言（网络不一定很好，而我们又不能一直等），所以JavaScript中的get之后往往有一个then() -- then是一种promise。 |
| Day 5 - 02 Intro to Databases              | [doc link](https://docs.google.com/presentation/d/1Xo5t1NXllDEiFmrcLF1GO8EH3JqrX_YAjY-Zf30dldQ/edit#slide=id.g4b9be9a1de_0_45) | [video link](https://www.youtube.com/watch?v=7q9CD2qOKEg) | MongoDB -- Document Database -- NoSQL -- Stores “documents”, which are basically JSON objects<br/><br/>针对我们之前的数据，其在MongoDB中的架构是：![image-20220401130517844](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204011305941.png)<br><br/>在云上运行MongoDB，我们用Atlas。<br> |
| **Day 5 - 03 W6: Databases Workshop**      | [doc link](https://docs.google.com/presentation/d/1F1CPOt2PICVBSabAu5NqDBmqdl3epgp88yOGereh5i4/edit?usp=sharing) | [video link](https://www.youtube.com/watch?v=rggO4Zbr-8g) | **关于MongoDB的数据库架构、配置、使用 —— 需要数据库、以及在web项目中使用的时候可以复习这个W6**<br/> |
| Day 5 - 05 Intermediate CSS                | [doc link](https://docs.google.com/presentation/d/1VDNsfe4ihBZ7XqiB-KMSrgSe5JaW0jjnx9l-21gETYQ/edit?usp=sharing) | [video link](https://www.youtube.com/watch?v=0qlpVv86d04) | Advanced CSS，如果想看实操，从video的16:20开始               |
|                                            |                                                              |                                                           |                                                              |
| Day 6 - 01 Recap                           | [doc link](https://docs.google.com/presentation/d/1JVEWEa-ADTuRQYzRSqLkLRTdDuCfX65mavY2_Q74UGQ/edit?usp=sharing) | [video link](https://www.youtube.com/watch?v=dF2imSTRRZM) | 关于Javascript代码中的数据更新<br>1）因为异步，所以加上then<br>2）因为React will re-run when props or states change，所以加上 useEffect确保不无限循环 |
| **Day 6 - 02 Accounts and Authorization**  | [doc link](https://docs.google.com/presentation/d/1mdAn2yHEmJSKxrUmj0VF-NCQk9iz2OOuAsoqQJXIzV8/edit?usp=sharing) | [video link](https://www.youtube.com/watch?v=EbI7LcpkDQI) | 代码部分从17:04开始，可重看                                  |
| Day 6 - 03 W8: Chatbook -- Sockets Part 1  | [doc link](https://docs.google.com/presentation/d/15G8C7sPFHbPgZoBPtpyGHAZTZTYxAqRsTZ7FpuOi0yY/edit?usp=sharing) | [video link](https://www.youtube.com/watch?v=NIZHluDVIO0) | 开头有一个精彩的Recap<br><br/>                               |
| Day 6 - 05 Sponsor Lecture: Ramp           |                                                              | [video link](https://www.youtube.com/watch?v=xYDCFweCETQ) |                                                              |
|                                            |                                                              |                                                           |                                                              |
| Day 7 - 01 W9: Chatbook -- Sockets Part 2  | [doc link](https://docs.google.com/presentation/d/1UzVo7y3NtoRunojbiJN7_7ijAWuTqtNmlSOe1C05WdQ/edit?usp=sharing) | [video link](https://www.youtube.com/watch?v=ZEU7tkbs5N0) |                                                              |
| Day 7 - 03 Advanced React                  | [doc link](https://docs.google.com/presentation/d/19TD2E9N-s1SoiPN441CH3T0nK4oJJpaUsyL0gM5uqJI/edit?usp=sharing) | [video link](https://www.youtube.com/watch?v=Ki0Bst-c8NI) |                                                              |
| Day 7 - 04 Sponsor Lecture: Next Jump      |                                                              | [video link](https://www.youtube.com/watch?v=UnJWIHE6N5g) |                                                              |
|                                            |                                                              |                                                           |                                                              |
| Day 8 - 01 How to Code Good                | [doc link](https://docs.google.com/presentation/d/1yfAfQMboPYYbhJZwkVhoIm65XniYa7y3b-H11n-vmo8/edit?usp=sharing) | [video link](https://www.youtube.com/watch?v=ghggCY6jnls) |                                                              |
| Day 8 - 02 Async Await                     | [doc link](https://docs.google.com/presentation/d/15l0B5yuKDmwOXaJRToaOBH2tFuag298OcBMGBL5je-o/edit?usp=sharing) | [video link](https://www.youtube.com/watch?v=ycLdTyW5aX8) |                                                              |
| Day 8 - 03 Sponsor Lecture: Cresicor       |                                                              | [video link](https://www.youtube.com/watch?v=cXgNampxat8) |                                                              |
| Day 8 - 04 Sponsor Lecture: Meta           |                                                              |                                                           |                                                              |
|                                            |                                                              |                                                           |                                                              |
| Day 9 - 01 Typescript                      | [doc link](https://docs.google.com/presentation/d/1KTqmPauDkLsWbXpOuU7rWv-mRfpIpIQMUpLrHqiqhV8/edit?usp=sharing) | [video link](https://www.youtube.com/watch?v=xM2jHBas--k) |                                                              |
| Day 9 - 02 Sponsor Lecture: Gather         | [doc link](https://docs.google.com/presentation/d/1T4ru16EPyVOIRfkSNQmd0o72cORiZaLcc7JbDq4kifc/edit?usp=sharing) | [video link](https://www.youtube.com/watch?v=K2DkJjNV0F0) |                                                              |
| Day 9 - 03 Libraries                       | [doc link](https://docs.google.com/presentation/d/1xOshZoMwC-zcBFXGoGm-TuJKSLvSi7sKkPoOgbg7jy4/edit?usp=sharing) | [video link](https://www.youtube.com/watch?v=SHYfViy9DII) |                                                              |
| Day 9 - 04 Sponsor Lecture: Bloomberg      |                                                              | [video link](https://www.youtube.com/watch?v=6YidhgHqCKY) |                                                              |
|                                            |                                                              |                                                           |                                                              |
| Day 10 - 01 How to Design Good             | [doc link](https://docs.google.com/presentation/d/1psreRusUehLs2U9qvsvVG6scv4oCOI4oAuU4LbnK3-I/edit?usp=sharing) | [video link](https://www.youtube.com/watch?v=W12JhbmLKXQ) |                                                              |
| Day 10 - 02 Sponsor Lecture: Appian        |                                                              | [video link](https://www.youtube.com/watch?v=0iO-tdj3AGI) |                                                              |
| Day 10 - 03 Sponsor Lecture: Open Learning |                                                              | [video link](https://www.youtube.com/watch?v=rgQsvdd2gmE) |                                                              |
| Day 10 - 04 How to Deploy                  | [doc link](https://docs.google.com/presentation/d/1wcdTK1M3Wu8e_RaY3sXHJG0ZN0KHS2-sjXlNVMjN6gw/edit?usp=sharing) | [video link](https://www.youtube.com/watch?v=oxJwXtybaZA) |                                                              |
| Day 10 - 05 How to Win WebLab + Sendoff    | [doc link](https://docs.google.com/presentation/d/1OJxEvZSbVjn1gnuhixW-8hRhKfqb5zbuJOiJ7Oe0BQI/edit?usp=sharing) | [video link](https://www.youtube.com/watch?v=notEk6eow5c) |                                                              |

## requirements

确保您的站点满足这些[基本要求](https://weblab.mit.edu/about/#rules)。

## details

## 您的网站必须满足所有基本要求

- **动态生成的、数据库支持的页面。**

您的站点必须包含由某些服务器端应用程序（例如 Node.js、Ruby on Rails、PHP 或 Python 脚本）使用对某些数据库或其他数据服务的查询结果动态生成的页面。你应该使用 MongoDB——我们在课堂上教的——或者如果你想使用其他东西，请先与工作人员确认。

- **基于用户帐户的个性化体验。**

您的网站必须具有登录功能。您可以实现自己的用户名/密码登录系统或使用现有系统（例如 Facebook 或 Google 登录）。网站的内容和/或 UI 应反映用户是否登录并显示一些重要的用户特定内容。您不需要实施帐户管理（例如密码恢复）。注意：如果您的网站使用 MIT 证书，您必须为我们的非 MIT 评委实施另一种身份验证形式。

- **原创设计和实施。**

您网站的高级设计和关键功能的实现必须是原创的。您可以使用 Web 应用程序框架（如 Express.js 或 Ruby on Rails）以及前端框架（如 Bootstrap 和 Backbone）。您可以使用开源组件，只要顶层设计是原创的，并且您网站的主要功能不仅仅是组件的包装。您不得为您的网站定制 CMS 系统，例如 Wordpress。



## 您的网站必须帮助用户访问大量内容。

- **预生成的数据集。**

您的数据库包含可公开访问的数据集的处理版本，或者您可以使用假数据引导您的网站。如果您选择通过生成数据来引导您的网站，请发挥创意！评委们会对一个到处都出现相同三个名字的网站感到厌烦！

- **第三方数据访问。**

您的系统使用另一个应用程序的可公开访问的 API 来动态访问和返回数据。您必须声明您使用的所有第 3 方 API。如果你走这条路，你应该使用数据库作为 API 请求的缓存和回退机制。如果您的应用程序在提交截止日期后由于第三方 API 损坏而出现故障，您将被取消资格。



## 您的网站必须包含一些重要的前端功能。在高层次上，这意味着您的站点不能简单地由服务器返回的页面组成，而是必须支持某种动态的用户交互。这里有一些建议

- **数据可视化。**

您的应用程序以可视化方式呈现数据，从而增强用户对数据的理解。可视化应该突出显示数据中一些不明显或不重要的特征。用户必须能够影响在可视化中显示哪些数据。您可以为您的可视化使用预先存在的实现，例如 jQueryUI 小部件，只要它适合您的应用程序。请记住，必须引用所有小部件和库。

- **动态过滤。**

您的应用程序会显示当前与用户最相关的一小部分（< 10%）数据子集，或者对数据进行排序以使最相关的项目首先显示。数据的子集和/或顺序必须响应用户的操作而改变。满足此要求的三个示例是全文搜索、基于条件的搜索和“为您推荐”部分。对于后者，您必须让我们相信内容会根据用户操作而变化。

- **异步查看/修改数据。**

加载应用程序后，以后的添加、修改或删除将异步完成（无需加载新页面）。包含通过异步调用服务器实现的重要功能的“单页应用程序”将满足此要求。



**[团队必须使用版本控制并在Github](http://github.com/)上托管源代码。我们的员工将为每个团队创建存储库，并教授如何使用 Github。**
