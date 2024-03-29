# "EARN IT大学生钱袋网"项目建模总结 & Git使用总结

{:.no_toc}

[TOC]

## 1、作者

- 学号：16340203
- 姓名：谭江华

## 2、建模总结

- 在软件开发过程中，我们需要完成需求文档的编写以及对具体功能进行建模。

- 这里我采用的是**umlet**这个软件进行建模画图。该软件可以满足各类需求规格的编写，例如在本次项目中有如下几个模型：

  - 用例图，业务过程/多泳道图
  - 用例活动图
  - 领域模型
  - 状态模型
  - 功能模型
  - BCE用例设计

  ![pic](pics/1.png)

- 用例图，业务过程/多泳道图：

  - 用例图主要是用来图示化系统的主事件流程，它用来描述客户的需求，即用户希望系统具备的完成一定功能的动作。并且由于一个系统中往往有**不同的用户对象**，他们所需的功能也不尽相同，因此在用例图都需要将这些显示出来。
  - 并且系统的基本功能一般用<<include>>展开，而一些额外的功能，则需要用<<extend>>进行展开。
  - 除了主系统之外，一般还有可能有其他**第三方接口或者系统**来帮我们实现一些功能，例如支付的时候可能用到第三方的支付系统等等。这些也需要在用力图中进行展示。
  - 例子![pic](F:/%E5%A4%A7%E4%B8%89%E4%B8%8B/%E7%B3%BB%E7%BB%9F%E5%88%86%E6%9E%90%E4%B8%8E%E8%AE%BE%E8%AE%A1/pics/usecase_diagram.png)

- 用例活动图：

  - 用例活动图则是对用例图中各个基本功能进行展开，具体地建模。
  - 用例活动图一般由**主成功场景事件流**和**拓展事件流**两部分组成。主成功场景事件流一般是该功能成功的运行步骤，而拓展事件流可能包括一些失败的事件以及突发事件。
  - 例子
  - ![pic](pics/usecase.png)

- 领域模型：

  - 从领域模型开始，就开始了面向对象的分析和设计过程，领域模型是完成从需求分析到面向对象设计的一座桥梁。

  - 建立领域模型需要发现**类**和**对象**。

  - 识别类的方法有：概念类分类列表，识别名词性短语。

  - 识别出来之后要建立类之间的关联：关联、继承、依赖。

  - 最后要添加类的一些重要属性：类的语义完整性、类的作用、问题域相关特性等。

  - 例子

    ![pic](pics/domain.png)

- 状态模型：

  - 状态模型用来描述一个特定的对象所有可能的状态,以及由于各种事件的发生而引起的状态之间的转移和变化。

  - 一般由这几部分组成：状态名(name)、进入/退出动作(entry/exit action)、内部转移(internal transttion)、子状态(substate)、延迟事件(dferred event)。

  - 例子

    ![pic](pics/state.png)

- 功能模型：

  - 功能模型是在描述某个具体功能时，以用户的角度对其进行展示。

  - 例子

    ![pic](pics/system.png)

## 3、Git使用总结

- 使用git可以很方便地对本地仓库和远程仓库进行管理同步。比起在github网页一项项地增添删改，效率会更加高。
- Git使用https协议每次pull/push都要输出密码，但如果使用git协议，再使用ssh密钥，就可以免去这一个麻烦的步骤，初次使用git协议大致需要三个步骤：
  - 生成密钥对
  - 设置远程仓库(例如github）上的公钥
  - 把git的remote url修改为git协议
- 本次项目我主要是使用git bash进行操作，由于是多人对仓库进行操作，所以一开始每次我push前都忘记先pull一遍下来，会导致各种merge的情况发生，即本地仓库的内容未改，然而远程仓库已经被其他人修改过了，我这个时候去add内容并commit就会导致merge的情况，会使得push失败。解决这个merge我使用的是两种方法：
  - 一种是直接打开产生merge的文件，手动对其进行修改，修改完之后再commit，解决merge问题。
  - 另一种是使用git log查看所有的历史版本，然后获取我们需要的历史版本id，使用”git reset --hard 版本id“进行回退。

