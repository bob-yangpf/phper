# git commit规范

## 为什么需要规范

1. 团队开发时候,规范可以团队的产出更多的去个性化,向团队化. 除了常见的代码规范,commit message规范也必不可少
2. 统一的commit message也是除了代码注释之外,其他对变更的说明,便于后续维护,提高团队效能
3. 规范的commit message 可以很方便的提炼出更新日志

## AngularJS提交规范

AngularJS提交规范 逐渐被大家认可,也成为了通用的提交规范. 所以本文主要使用的规范对象统一指 `AngularJS提交规范`

他可以通过可以通过工具 [commitizen](https://www.npmjs.com/package/commitizen) 进行一些模板和

[AngularJS](https://github.com/angular/angular/commits/master) 在 github上 的提交记录被业内许多人认可，逐渐被大家引用。



##  规范详情

每次提交，Commit message 都包括三个部分：Header，Body 和 Footer

### Header

Header 部分只有一行,包含三个部分 **type** `(必须)`, **scope**`(选填)`和**subject**`(必填)`

####  (1) type

用于说明commit的类别,只允许使用以下标识

> 
>   - 主要type
>       feat:     增加新功能
>     fix:       修复bug
>   
>   - 特殊type
>       docs:     只改动了文档相关的内容
>     style:    不影响代码含义的改动，例如去掉空格、改变缩进、增删分号
>     build:    构造工具的或者外部依赖的改动，例如webpack，npm
>     refactor: 代码重构时使用
>     revert:   执行git revert打印的message
>   
>   - 暂不使用type
>       test:     添加测试或者修改现有测试
>     perf:     提高性能的改动
>     ci:       与CI（持续集成服务）有关的改动
>     chore:    不修改src或者test的其余修改，例如构建过程或辅助工具的变动
> 

如果`type`为`feat`和`fix`，则该 commit 将肯定出现在 Change log 之中。其他情况（`docs`、`chore`、`style`、`refactor`、`test`）由你决定，要不要放入 Change log，建议是不要。

#### (2) scope

`scope`用于说明 commit 影响的范围，比如数据层、控制层、视图层等等，视项目不同而不同。

#### (3) subject

`subject`是 commit 目的的简短描述，不超过50个字符。

> * 以动词开头,使用第一人称现在时,比如change,而不是changed或者changes
> * 第一个字母小写-汉语忽略
> * 结尾不加句号(.)

### Body

Body 部分是对本次 commit 的详细描述，可以分成多行。下面是一个范例。

```wiki
More detailed explanatory text, if necessary.  Wrap it to 
about 72 characters or so. 

Further paragraphs come after blank lines.

- Bullet points are okay, too
- Use a hanging indent
```

有两个注意点。

（1）使用第一人称现在时，比如使用`change`而不是`changed`或`changes`。

（2）应该说明代码变动的动机，以及与以前行为的对比。



### Footer

Footer 部分只用于两种情况。

**（1）不兼容变动**

如果当前代码与上一个版本不兼容，则 Footer 部分以`BREAKING CHANGE`开头，后面是对变动的描述、以及变动理由和迁移方法。

 ```bash
 BREAKING CHANGE: isolate scope bindings definition has changed.
 
     To migrate the code follow the example below:
 
     Before:
 
     scope: {
       myAttr: 'attribute',
     }

     After:
 
     scope: {
       myAttr: '@',
     }
 
     The removed `inject` wasn't generaly useful for directives so there should be no code using it.
 ```

**（2）关闭 Issue**

如果当前 commit 针对某个或者多个issue

```bash
 Closes #123, #245, #992
```

### Revert

还有一种特殊情况，如果当前 commit 用于撤销以前的 commit，则必须以`revert:`开头，后面跟着被撤销 Commit 的 Header。

```bash
revert: feat(pencil): add 'graphiteWidth' option

This reverts commit 667ecc1654a317a13331b17617d973392f415f02.
```

Body部分的格式是固定的，必须写成`This reverts commit <hash>.`，其中的`hash`是被撤销 commit 的 SHA 标识符。

如果当前 commit 与被撤销的 commit，在同一个发布（release）里面，那么它们都不会出现在 Change log 里面。如果两者在不同的发布，那么当前 commit，会出现在 Change log 的`Reverts`小标题下面。

# 如何使用

## 其他

## 引用

1 .[阮一峰的博客]( http://www.ruanyifeng.com/blog/2016/01/commit_message_change_log.html)

2.[知乎:关于 Git 提交这些规范，你都遵守了吗？](https://zhuanlan.zhihu.com/p/88870009)

3 [Contributing to Angular](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines)