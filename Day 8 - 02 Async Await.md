# Day 8 - 02 Async Await -- 异步



## Promise -- key concept

![image-20220406155712583](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204061557795.png)

## then()

![image-20220406155741113](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204061557222.png)

## catch()

![image-20220406155800706](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204061558810.png)

## Chaining promises

![image-20220406155831200](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204061558476.png)

## Async and Await -- why Await

![image-20220406160128783](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204061601876.png)

- You can’t do computation with pending promises
- Wait for the promise to resolve
- Get the value that it resolves to

![image-20220406160223494](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204061602595.png)

但是实际上是报错 原因是：只有异步函数可以await，所以我们应该写如下函数：

![image-20220406160549949](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204061605078.png)

并且外部也需要改：

![image-20220406160844321](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204061608431.png)

## Recap -- Async and Await

![image-20220406163052233](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204061630327.png)



## 实际应用中 —— 多个promises —— 还有race() any()

![image-20220406161213711](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204061612811.png)

下面的 Returns a promise that resolves to array of results of input promises

![image-20220406161224303](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204061612392.png)

下面的 Returns a promise that fulfills or rejects with the first promise that fulfils or rejects

![image-20220406161249056](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204061612147.png)

下面的 Returns a promise that resolves when any of the input promises fulfills

![image-20220406161308161](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204061613298.png)



## Why Async？为什么需要异步？

因为我们不能保证在多个机器之间传输数据需要多长时间，所以我们不敢一直等待。

 

## JavaScript Event Loop

比如玩页面游戏的时候，无论什么时候，我们按上下左右键，人物都会移动，这就是一个隐藏的Loop所完成的功能。这就是由异步完成的，因为如果是同步，一旦一个操作卡了就什么也做不了了。—— 所以异步能够保证网站的响应能力。

![image-20220406162123708](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202204061621811.png)



## 总结

Promises是JavaScript异步的核心。















