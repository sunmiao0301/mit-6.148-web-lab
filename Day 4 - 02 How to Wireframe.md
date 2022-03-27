# Day 4 - 02 How to Wireframe 



## First: Review ---- ↓

## Router

![image-20220327181721203](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203271817400.png)



## useEffect, get requests

首先看下面的代码，首先通过get的得到天气情况，然后通过setWeather函数将拿到的天气情况放入weather值中，但是实际情况并非如此：get函数是异步的，那么从服务器请求得到结果也是需要时间的，那么setWeather函数运行的时候，get函数还没从服务器拿到最新的天气数据，也就更新了错误的值。

![image-20220327182303505](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203271823639.png)

解决这个问题的办法如下，可以解释为：**You get the weather, and then you set the weather to be what you received...**也就是等待这个异步函数完成之后，再继续执行then...

![image-20220327183130162](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203271831381.png)

但是这还不够，因为在React中，Component will re-run their code whenever state or props changes，也就是说，我们上面写的get函数，得到了一个新的state值并且set，会导致触发组件的re-run，然而组件re-run之后，这个get函数又会再次执行，就这样互相影响，导致了无限执行的循环。

解决方案如下：

![image-20220327184112058](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203271841190.png)

以上就是Review，总结成图片如下：

![image-20220327184323186](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203271843341.png)



## Now: Design and Wireframing! 设计、描框 —— UI & UX ——UI的炫酷不代表好用

![image-20220327192603853](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203271926072.png)

## how do i make a wireframe?

- figma !!! (website)
- google slides
- any wireframe software / Photoshop / Sketch / etc.















