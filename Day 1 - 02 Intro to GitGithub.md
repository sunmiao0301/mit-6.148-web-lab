# Day 1 - 02 Intro to Git/Github

1、文件同步 —— 每个人都应该知道哪个文件是最新的

2、文件协作 —— 每个人的修改都能被加入

3、版本控制 —— 找到过去的版本



p.s 我们希望在**本地**进行编程，然后在完成特定部分后合并更改。



### Git如何追踪修改？

我们通过跟踪加减行集合，来完成追踪。



一些名词：

Repository：代码，是我们正在追踪的代码文件

Commit：一堆打包起来的修改 a packaged set of changes  

Log：日志，提交历史

push：将commits提交到git服务器

pull：从git服务器上取得最新的代码文件



### 我们如何合并（merge）？

假设现在有一个main分支，然后ben和Alice同时拿到了main分支，然后ben速度比较快，对main分支做完修改之后push上传到了git server上，此时Alice也做完了修改，此时Alice想直接push是不行的，必须pull拿到ben修改完的main，并且和自己本地main进行merge，然后才能push上传。



### 合并冲突

ben修改了代码的第四行，Alice也修改了第四行，那么当Alice用pull拉取ben新上传的main时，就会发生冲突，此时git server会提醒你进行手动合并。合并之后，再push就行了。



### 命令行



### git log









