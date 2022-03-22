# MIT-6.148-Web-Lab

### about web.lab

learn how to build a dynamic, server-backed website.

### what is web.lab

A 6-Unit MIT IAP Class which teaches the fundamentals of web development.

### class structure

we walk through the basics of web development: how to program in **HTML**, **CSS**, and **JavaScript**, how to **launch a backend server using node.js**, and how to **integrate a database into your web-app using MongoDB**. In the second week, we teach **more advanced topics and sponsors** give cool lectures on how students can utilize industry techniques and technoligies in their project.

### schedule

https://weblab.mit.edu/schedule/

Week 1 - we build an app from scratch together!

Week 2 - advanced topics + sponsor lectures

Week 3 - code, code, code 

Week 4 - Code, Code, Code

### resources

https://weblab.mit.edu/resources/

### requirements

确保您的站点满足这些[基本要求](https://weblab.mit.edu/about/#rules)。



### details

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
