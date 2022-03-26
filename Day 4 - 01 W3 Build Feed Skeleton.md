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















































