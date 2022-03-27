# Day 4 - 01 W3: Build Feed Skeleton —— More React, Using APIs, and Routing

这次的workshop，我们将要做的是：将我们的catbook与API相连接，然后还会做一些routing（因为我们的网站会有不止一个界面，所以我们会通过路由routing来完成不同页面的转换）

## git reset --hard

将代码恢复到你上一次从云（此处是github）上拿到的代码

## git checkout wX-stepY



## 过去，我们做了？

1）通过React构建Profile page --> 组件，以及组件的Props、State

2）API、HTTP、异步编程。



## 这次，我们将：

1）对React更加熟悉

2）与前端的API相交互（p.s. 我们在这节课不会去构建API，只是去调用别人已经写好的API，后面我们会自己构建API，然后自己调用） —— GET、POST（我们将通过API端点进行这两种操作）

![image-20220325183028280](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251830589.png)



## git checkout w3-starter

来到 w3 之后，我们可以看一下我们的代码结构，大部分与之前的 w2 没有区别，主要区别在于一个utilities.js文件，我们可以预览一下：

```javascript
/**
 * Utility functions to make API requests.
 * By importing this file, you can use the provided get and post functions.
 * You shouldn't need to modify this file, but if you want to learn more
 * about how these functions work, google search "Fetch API"
 *
 * These functions return promises, which means you should use ".then" on them.
 * e.g. get('/api/foo', { bar: 0 }).then(res => console.log(res))
 */

const BASE_URL = "http://catbook-workshop2.herokuapp.com";

// ex: formatParams({ some_key: "some_value", a: "b"}) => "some_key=some_value&a=b"
function formatParams(params) {
  // iterate of all the keys of params as an array,
  // map it to a new array of URL string encoded key,value pairs
  // join all the url params using an ampersand (&).
  return Object.keys(params)
    .map((key) => key + "=" + encodeURIComponent(params[key]))
    .join("&");
}

// convert a fetch result to a JSON object with error handling for fetch and json errors
function convertToJSON(res) {
  if (!res.ok) {
    throw `API request failed with response status ${res.status} and text: ${res.statusText}`;
  }

  return res
    .clone() // clone so that the original is still readable for debugging
    .json() // start converting to JSON object
    .catch((error) => {
      // throw an error containing the text that couldn't be converted to JSON
      return res.text().then((text) => {
        throw `API request's result could not be converted to a JSON object: \n${text}`;
      });
    });
}

// Helper code to make a get request. Default parameter of empty JSON Object for params.
// Returns a Promise to a JSON Object.
export function get(endpoint, params = {}) {
  const fullPath = endpoint + "?" + formatParams(params);
  return fetch(BASE_URL + fullPath)
    .then(convertToJSON)
    .catch((error) => {
      // give a useful error message
      throw `GET request to ${fullPath} failed with error:\n${error}`;
    });
}

// Helper code to make a post request. Default parameter of empty JSON Object for params.
// Returns a Promise to a JSON Object.
export function post(endpoint, params = {}) {
  return fetch(BASE_URL + endpoint, {
    method: "POST",
    headers: { "Content-type": "application/json" },
    body: JSON.stringify(params),
  })
    .then(convertToJSON) // convert result to JSON object
    .catch((error) => {
      // give a useful error message
      throw `POST request to ${endpoint} failed with error:\n${error}`;
    });
}

```

可以看到BASE_URL，是我们的url

```javascript
const BASE_URL = "http://catbook-workshop2.herokuapp.com";
```

然后是get()函数如下，用于在endpoint得到我们想要的数据，params是我们的参数。

```javascript
// Helper code to make a get request. Default parameter of empty JSON Object for params.
// Returns a Promise to a JSON Object.
export function get(endpoint, params = {}) {
  const fullPath = endpoint + "?" + formatParams(params);
  return fetch(BASE_URL + fullPath)
    .then(convertToJSON)
    .catch((error) => {
      // give a useful error message
      throw `GET request to ${fullPath} failed with error:\n${error}`;
    });
}
```

然后是post()函数如下，用于将我们的参数传递给服务器，以求post在服务器上

```javascript
// Helper code to make a post request. Default parameter of empty JSON Object for params.
// Returns a Promise to a JSON Object.
export function post(endpoint, params = {}) {
  return fetch(BASE_URL + endpoint, {
    method: "POST",
    headers: { "Content-type": "application/json" },
    body: JSON.stringify(params),
  })
    .then(convertToJSON) // convert result to JSON object
    .catch((error) => {
      // give a useful error message
      throw `POST request to ${endpoint} failed with error:\n${error}`;
    });
}
```

今天我们要实现的，比之前要困难很多，app结构如下：

![image-20220325184427927](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251844193.png)

其中，Card是一个包含帖子以及其评论的组件。



## 思考需求

- 我们应该可以看帖 也就是 GET 功能
- 我们应该可以发帖（也就是发到后端） 也就是 POST 功能
- 最后是前端路由，因为我们会有多个前端页面。

## npm run hotloader && head to localhost:5000 in your browser

**下面我们尽量一步步讲解，这个项目还是比较有意义的，算是一个简陋的前后端。**

首先是在App.js中导入我们的Feed组件。

![image-20220325185848881](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203251858013.png)

```javascript
import feed 
```



## GET



## POST



## 页面路由

页面路由，也就是当我们访问不同的url，我们会导航到不同的页面之下，比如访问catbook.com就会导航到主页，访问catbook.com/profile就会导航到个人资料等等。

![image-20220325214611969](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203252146104.png)

为了实现这一点，我们需要用一个库叫做 —— **Reach Router library**，后面我们将具体实操一下，最终的结果应该如下，也对应我们上一张图里面的三个url。

![image-20220325215052516](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203252150606.png)



## git checkout w3-step5 —— 页面路由

首先要做的第一件事就是**导入`import { Router } from "@reach/router"`**（此外，也导入了我们需要的其他页面的component —— NotFound

然后在js的html环境中，将App.js返回如下：

```javascript
const App = () => {
 return (
   // <> is like a <div>, but won't show
   // up in the DOM tree
   <>
     <NavBar />
     <div className="App-container">
       <Router>
         <Profile path="/profile" />
       <Feed path="/"/>
         <NotFound default/>
       </Router>
       {/* TODO (step5): use Router to route between pages */}
     </div>
   </>
```

然后我们访问 localhost:5000 就可以看到：

![image-20220327114222645](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203271142850.png)

然后根据我们设定的路由规则，我们访问 localhost:5000/profile

![image-20220327114310407](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203271143529.png)

或是访问一个不存在的路由页面：localhost:5000/pro

![image-20220327114437191](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203271144281.png)



到了这一步，我们就能很自然的想到下一步：如果用户访问一个网站，每次都需要手动在 url 栏输入/profile 等路径，太不友好的，我们应该在主页上加上这些路径，让其可点击。 很自然的，这些导航标签应该在NavBar中，所以我们首先**在NavBar导入一个`import { Link } from "@reach/router";`**

然后js中html环境返回如下：

```javascript
const NavBar = () => {
  return (
    <nav className="NavBar-container">
      <div className="NavBar-title">Catbook</div>
        <Link to="/">Home</Link>
            <Link to="/profile">Profile</Link>
      {/* TODO (step5): implement links to pages */}
    </nav>
  );
};
```

此时，我们就可以通过这两个Home、Profile标签进行导航了：

![image-20220327115448758](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203271154872.png)

但是此时，几个导航的按键位置还不够理想，我们对其加上css如下：

```javascript
const NavBar = () => {
  return (
    <nav className="NavBar-container">
      <div className="NavBar-title u-inlineBlock">Catbook</div>
        <div className="NavBar-linkContainer u-inlineBlock">
        <Link className="NavBar-link" to="/">Home</Link>
            <Link className="NavBar-link" to="/profile">Profile</Link>
        </div>
      {/* TODO (step5): implement links to pages */}
    </nav>
  );
};
```

结果如下：

![image-20220327115916194](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203271159343.png)



## git checkout w3-step6

在上面，我们已经完成了stories的设计，下面让我们进行comment部分。因为comment和 card的相似性，我们的step6-8会和step1-4非常相似。

但是需要注意的是，我们之间在网站的Home页面显示Card.js的时候，调用的GET的API是无参数的，因为我们显示了后端所有的评论，但是评论部分不能这么做，因为我们针对特定的帖子，应该是一个特定的评论而不是后端所有的评论都在一个帖子下面。

同理，我们当时进行的POST也是只有一个 评论内容 的参数，但是这次我们想加上一个父级帖子的参数，这样我们就能保证帖子和评论的对应关系，知道每个帖子下面应该有哪些评论。

具体差别如下：

![image-20220327121027581](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203271210735.png)



在第六步中，我们通过get完成了评论的导入，下面让我们进入step7

 ## git checkout w3-step7

第七步需要我们自己动手，在Card.js中实现<SingleComment (props) /> （就像我们之前在Feed.js中实现Card.js一样），实现的最终结果应该如下所示：

![image-20220327125605243](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203271256378.png)



## git checkout w3-step8

这一步我最终完成如下：

![image-20220327151328836](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203271513204.png)



## git checkout w3-step9

在第9步中，我们需要完成的是一个符合React思想的优化，我们的Card.js目前是直接包含SingleStory + commentsList + NewComment。在这一步中，我们需要将 commentsList + NewComment 剥离出来，形成一个CommentBlock，然后CommentBlock 之下才是 commentsList + NewComment 。

最终的结果应该是：

![image-20220327152005873](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203271520104.png)

我最终实现的结果如下：

![image-20220327153223782](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203271532891.png)



























