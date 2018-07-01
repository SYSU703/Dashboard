# 15331029 系统分析与设计 项目报告
## 简短的课程学习自我总结（400字以内）
在我们小组开发的FastChat项目中，我负责前端开发工作。在这个过程中，围绕着vue，我学习了一系列的前端工具和类库，并且自己搭建起了一套完整的开发环境和部署环境，包括：
* 轻量高效的运行时支持库：vuejs + vuex + vue-router + vue-resource + iview组件库。
* 低容错性的开发环境：typescript + vetur + eslint + tslint。
* 现代化的构建工具：@vue/cli (webpack + vue-loader + ts-loader + babel-loader + ……)。
* 便捷的容器化部署：docker。
我花了相当长的时间来纠结环境的配置。但是在配置这些工具的过程中，我终于知道了这些工具到底是如何运作的。

除了学习新工具以外，我还在前端架构的设计上下了很多功夫：
* 为了做到“一个前端兼容多个后端”，我将前端的**数据获取**操作封装成了一个抽象类：[serviceAgent](https://github.com/SYSU703/fastchat-fe/blob/master/src/serviceAgent/interfaces.ts)，fastchat-fe仅仅依赖于这个**抽象类接口**，而不依赖于具体的数据获取功能**实现**（得益于typescript的引入，在前端可以做到抽象类型设计）。
* 另外，为了将简洁性和可扩展性最大化，fastchat-fe本身**并不主动获取**数据的更新(比如获取新消息)，而是通过发布-订阅模式，**订阅**数据的更新，**抽象类的实现者**在自己认为适当的时候调用callback来告知新数据。这样，抽象类的实现者既可以通过轮循服务端来知晓数据更新，也可以通过server push、websocket等方式。

## PSP 2.1 统计表

|         PSP 2.1          |               How to do                | Time(hours) |
| :----------------------: | :------------------------------------: | :---------: |
|         Planning         |                  计划                  |      4      |
|         Estimate         |         估计自己的任务所需时间         |      2      |
|       Development        |                  开发                  |    45     |
|         Analysis         |                分析需求                |     8      |
|       Design Spec        |              生成设计文档              |     6      |
|      Design Review       |     设计复审（和同事审核设计文档）     |      4      |
|     Coding Standard      | 代码规范（为目前的开发制定合适的规范） |     3     |
|          Design          |                具体设计                |      15      |
|          Coding          |                具体编码                |      20      |
|       Code Review        |                代码复审                |      2      |
|           Test           |  测试（包括自测，修改代码，提交修改）  |      3      |
|       Test Report        |                测试报告                |      0      |
|          Report          |                  报告                  |      4      |
|     Size Measurement     |               计算工作量               |      0      |
|        Postmortem        |                事后总结                |      2      |
| Process Improvement Plan |            提出过程改进计划            |      2      |
|           Sum            |                  合计                  |    120    |

## 个人分支的 GIT 统计报告
前端项目贡献：
![fastchat-fe](/images/fastchat-fe-contribution.png)

另外，为了验证数据获取抽象化的成果，我还写了一个简单的php+codeigniter后台项目：[fastchat-se](https://github.com/csr632/fastchat-se)。
![fastchat-se](/images/fastchat-se-contribution.png)
行数不准确，codeigniter(php框架)本身的代码被算上了。

## 自认为最得意/或有价值/或有苦劳的工作清单
1. 前端环境、工具链配置。由于vue、vuex对typescript的支持还不太友好，因此在这个过程中解决了不少困难。
2. 设计了一套简单易用的前后端通信接口（RESTful API）。将数据通信归纳为对4种领域模型的操作：session、user、friend、chat。详见[fastchat-se](https://github.com/csr632/fastchat-se)。
3. 前端架构设计：抽象的数据获取类、发布-订阅模式。
4. 通过docker+nginx来部署前端静态资源。

## 个人的技术类、项目管理类博客清单
[详解REST架构风格](https://segmentfault.com/a/1190000014768057)
[【linux】与 用户、权限 有关的常用命令](https://segmentfault.com/a/1190000015228684)
[【docker】 bind-mount或者COPY时需要注意 用户、文件权限 的问题](https://segmentfault.com/a/1190000015233229)
[【docker】小技巧：在宿主机器上直接查看docker容器的进程](https://segmentfault.com/a/1190000015238535)
[用css控制元素高度：自底向上和自顶向下的方法](https://segmentfault.com/a/1190000015309390)
