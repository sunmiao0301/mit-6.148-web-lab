# Day 2 - W1: Javascript

构建一个名为贪吃蛇的简单游戏 - Make Something With JS



### 思考我们需要什么：

1、Game setup

2、Snake

3、Respond to inputs

4、Food

5、Snake die



## 首先是进入catbook-react，然后git checkout w1-starter

在网页上打开html文件，可以看到如下页面：

![image-20220323184828045](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231848149.png)

然后让我们检查一下html，我们可以看到这个game-board是一个正方形，且有很多小方块在其中。

![image-20220323185133614](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231851706.png)

做到这一步，我准备打开js文件的时候，js变成了只读文件，无法被编辑，如果要编辑，会提示报错为：File doesn't belong to this project，相关解决方案是：

```wiki
If someone is experiencing this problem with the PhpStorm 2021 version, try these steps:

1. Close the IDE.
2. Go the project directory and delete .idea folder.
3. Restart the IDE.

For me, the IDE created a new .idea folder and recognized all files as the part of the project.
```

然后我们可以转到js编辑如下：

```javascript
const main = () => {
    update();
    draw();
}

setInterval(main);

const update = () => {
    console.log("update");
}

const draw = () => {
}
```

然后在chrome中打开console，可以看到会无限，并且很快的报出：update，如下：

![image-20220323190410026](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231904107.png)

所以这就像我们调用它的频率一样，但是这个速度太快了，不利于我们管理它，所以我们改换一下主函数为`setInterval(main, 1000/5);`，由于是毫秒为单位，1秒是1000毫秒，那么1000/5就是1秒运行5次了：

```javascript
const main = () => {
    update();
    draw();
}

setInterval(main, 1000/5);

const update = () => {
    console.log("update");
}

const draw = () => {
}
```

此时我们再次运行，在console中可以看到运行频率慢下来很多，大概是1秒5次。



但是更好的实现方案是：

```javascript
const SNAKE_SPEED = 5;

const main = () => {
    update();
    draw();
}

setInterval(main, 1000/SNAKE_SPEED);

const update = () => {
    console.log("update");
}

const draw = () => {
}
```



## $ git checkout w1-step1

在这一部分，我们为蛇写了一个仅仅向下移动的功能，并且成功能运行，代码和结果如下：

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <link rel="stylesheet" href="style.css" />
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Snake</title>
    <script src="snake.js"></script>
    <script src="game.js" defer></script>
  </head>
  <body>
    <div id="game-board"></div>
  </body>
</html>
```



由于我们在html中，将两个js文件已经链接，所以两个js文件中的变量可以互相调用。



snake.js

```JavaScript
// TODO: fill me in!
const SNAKE_SPEED = 5;

const snakeBody = [
    {x:11, y:11},
    {x:11, y:10},
    {x:11, y:9}
];

const updateSnake = () => {
  // remove tail
  snakeBody.pop();

  // move the head
  const newHead = {...snakeBody[0]};
  newHead.x += 0;
  newHead.y += 1;

  snakeBody.unshift(newHead);
};

// Don't change this function!
const drawSnake = (gameBoard) => {
    for (let i = 0; i < snakeBody.length; i++) {
        const segment = snakeBody[i];
        const snakeElement = document.createElement("div");
        snakeElement.style.gridRowStart = segment.y;
        snakeElement.style.gridColumnStart = segment.x;
        snakeElement.classList.add("snake");
        gameBoard.appendChild(snakeElement);
    }
}
```



game.js

```javascript
const gameBoard = document.getElementById("game-board");

const main = () => {
    update();
    draw();
}

setInterval(main, 1000/SNAKE_SPEED);

const update = () => {
    console.log("Updating");
    updateSnake();
}

const draw = () => {
    gameBoard.innerHTML = "";
    drawSnake(gameBoard);
}
```



最终运行结果：

![image-20220323193851368](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202203231938484.png)



## $ git checkout w1-step2

我们需要做的下一件事，就是接受键盘输入，以便我们进行对应的响应。

加上一点东西，实现如下：

input.js —— 捕捉键盘动作，响应，并且能阻止180度的转弯。

```javascript
let inputDirection = { x: 0, y: 1 };
let lastInputDirection = { x: 0, y: 1 };

window.addEventListener('keydown', event => {
    if (event.key === "ArrowUp" && lastInputDirection.x !== 0) {
        inputDirection = { x: 0, y: -1 };
    } else if (event.key === "ArrowDown" && lastInputDirection.x !== 0) {
        inputDirection = { x: 0, y: 1 };
    } else if (event.key === "ArrowRight" && lastInputDirection.y !== 0) {
        inputDirection = { x: 1, y: 0 };
    } else if (event.key === "ArrowLeft" && lastInputDirection.y !== 0) {
        inputDirection = { x: -1, y: 0 };
    }

})

const getInputDirection = () => {
    lastInputDirection = inputDirection;
    return inputDirection;
}
```

snake.js

```javascript
const SNAKE_SPEED = 5;
const snakeBody = [
    {x:11, y:11},
    {x:11, y:10},
    {x:11, y:9}
];

const updateSnake = () => {
    // remove tail segment
    snakeBody.pop();

    // add new head segment
    const newHead = {...snakeBody[0]};
    const snakeDirection = getInputDirection();
    
    newHead.x += snakeDirection.x;
    newHead.y += snakeDirection.y;
// 这里还是很聪明的，贪吃蛇的本质的每一步，都只有蛇的头部和尾部发生了变化，其他部分没有变化。
    snakeBody.unshift(newHead);
}

// Don't change this function!
const drawSnake = (gameBoard) => {
    for (let i = 0; i < snakeBody.length; i++) {
        const segment = snakeBody[i];
        const snakeElement = document.createElement("div");
        snakeElement.style.gridRowStart = segment.y;
        snakeElement.style.gridColumnStart = segment.x;
        snakeElement.classList.add("snake");
        gameBoard.appendChild(snakeElement);
    }
}

```

game.js

```javascript
const gameBoard = document.getElementById("game-board");

const main = () => {
    update();
    draw();
}

setInterval(main, 1000/SNAKE_SPEED);

const update = () => {
    console.log("Updating");
    updateSnake();
}

const draw = () => {
    gameBoard.innerHTML = "";
    drawSnake(gameBoard);
    drawFood(gameBoard);
}

```



## $ git checkout w1-step3

下面让我们开始针对food，我们需要解决food问题，food问题在step4中得到解决。

## 具体实现见w1-step4

在step4中，主讲人已经实现完成food部分之后，我们需要考虑的是游戏结束问题，也就是Game Over的两种情况，具体实现见w1-step5

## $ git checkout w1-complete

























