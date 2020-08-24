# Git commit 提交规范

## commit message template
[Angular规范](https://github.com/angular/angular.js/blob/master/DEVELOPERS.md#-git-commit-guidelines)是目前使用最广泛的写法：
Each commit message consists of a header, a body and a footer. The header has a special format that includes a type, a scope and a subject:

```
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer> 
```

其中 type 的值(必选)可以有
* feat :新功能 
* fix/to ：修复bug,可以是QA发现的BUG,也可以是研发自己发现的BUG
* fix ：产生diff并自动修复此问题,适合于一次提交直接修复问题
* to ：只产生diff不自动修复此问题,适合于多次提交,最终修复问题提交时使用fix
* doc :文档改变
* style :代码格式改变
* refactor :某个已有功能重构
* perf :性能优化
* test :增加测试
* build :改变了build工具 如 grunt换成了 npm
* revert :撤销上一次的 commit 
* merge ：代码合并
* ...

scope(必选)用于说明 commit 影响的范围，比如数据层、控制层、视图层等等，视项目不同而不同。
* all :表示影响面大 ，如修改了网络框架  会对真个程序产生影响
* loation :表示影响小，某个小小的功能
* module :表示会影响某个模块 如登录模块、首页模块 、用户管理模块等等
* ...

subject(必选)是commit目的的简短描述，不超过50个字符，建议使用中文，结尾不加句号或其他标点符号。

body(可选)具体的修改信息，应该尽量详细。

footer(可选)放置备注，比如是 bug，可以把bug id放入

通常简化的提交信息只需要第一行即可，故新建如下的 git commit template:
```
<type>(<scope>): <subject>


# * feat :新功能 
# * fix/to ：修复bug,可以是QA发现的BUG,也可以是研发自己发现的BUG
# * fix ：产生diff并自动修复此问题,适合于一次提交直接修复问题
# * to ：只产生diff不自动修复此问题,适合于多次提交,最终修复问题提交时使用fix
# * doc :文档改变
# * style :代码格式改变
# * refactor :某个已有功能重构
# * perf :性能优化
# * test :增加测试
# * build :改变了build工具 如 grunt换成了 npm
# * revert :撤销上一次的 commit 
# * merge ：代码合并
# * ...
# 
# scope(必选)用于说明 commit 影响的范围，比如数据层、控制层、视图层等等，视项目不同而不同。
# * all :表示影响面大 ，如修改了网络框架  会对真个程序产生影响
# * loation :表示影响小，某个小小的功能
# * module :表示会影响某个模块 如登录模块、首页模块 、用户管理模块等等
# * ...
# 
# subject(必选)是commit目的的简短描述，不超过50个字符，建议使用中文，结尾不加句号或其他标点符号。
# 
# body(可选)具体的修改信息，应该尽量详细。
# 
# footer(可选)放置备注，比如是 bug，可以把bug id放入
```
根据以上规范git commit message将是如下的格式：
```
       fix(DAO):用户查询缺少username属性 
       feat(Controller):用户查询接口开发
```
保存为`.git_template`(自定义)，可放到根目录下，我放在`/Users/JunQiLiu/.git_template`,打开 git bash,输入命令

```
git config --global commit.template /Users/JunQiLiu/.git_template
```
![](2.png)
即可完成模板设置。

提交时，输入命令
```
git commit
```
将自动打开模板文档，可以在此输入你的提交信息：
![](4.png)

关闭后将完成提交:

![](5.png)

效果如下:
![](6.png)


## Git-flow 工作流
[sourcetree](https://www.sourcetreeapp.com/)集成了非常方便的git工作流功能，点击`Git工作流`按钮即可初始化仓库:
![](7.png)

### 开发新功能
点击创建新的功能，此时我们发现已经为我们创建了feature/news分支，我们将在此分支进行功能开发。
![](8.png)

### 开发完成
点击完成功能。 此时我们发现已经将feature/news分支合并到了develop分支。
![](9.png) 

![](10.png)

### 预发布 开始release
![](11.png)

### 发布 完成release

点击完成发布版本，此时我们发现已经将release/1.0.0分支合并到了develop和master

![](12.png)

### 线上问题修复 开始hotfix
点击创建新的修复补丁，此时我们发现基于master为我们创建了hotfix/v1.0.0-20191226

## 参考
[Angular规范](https://github.com/angular/angular.js/blob/master/DEVELOPERS.md#-git-commit-guidelines)

[Angular提交信息规范](https://zj-git-guide.readthedocs.io/zh_CN/latest/message/Angular%E6%8F%90%E4%BA%A4%E4%BF%A1%E6%81%AF%E8%A7%84%E8%8C%83/)

[如何规范你的Git commit？](https://zhuanlan.zhihu.com/p/182553920)

[git flow 简单入门 | SourceTree操作Git工作流](https://www.cnblogs.com/liuqitoday/p/12102791.html)
