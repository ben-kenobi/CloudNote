
# Markdown 语法

## 标题

语法：

```
# 第一级标题 `<h1>` 
## 第二级标题 `<h2>` 
###### 第六级标题 `<h6>` 
```

效果：

# 第一级标题 `<h1>` 
## 第二级标题 `<h2>` 
###### 第六级标题 `<h6>` 



## 强调

语法：

```
*这些文字会生成`<em>`*
_这些文字会生成`<u>`_

**这些文字会生成`<strong>`**
__这些文字会生成`<strong>`__
```

效果：

*这些文字会生成`<em>`*
_这些文字会生成`<u>`_

**这些文字会生成`<strong>`**
__这些文字会生成`<strong>`__

## 换行

四个及以上空格加回车     
        
        

## 列表

### 无序列表

语法：

```
* 项目一 无序列表 `* + 空格键`
* 项目二
    * 项目二的子项目一 无序列表 `TAB + * + 空格键`
    * 项目二的子项目二
```


效果：

* 项目一 无序列表 `* + 空格键`
* 项目二
    * 项目二的子项目一 无序列表 `TAB + * + 空格键`
    * 项目二的子项目二

### 有序列表

语法：

```
1. 项目一 有序列表 `数字 + . + 空格键`
2. 项目二 
3. 项目三
    1. 项目三的子项目一 有序列表 `TAB + 数字 + . + 空格键`
    2. 项目三的子项目二
```

效果：

1. 项目一 有序列表 `数字 + . + 空格键`
2. 项目二 
3. 项目三
    1. 项目三的子项目一 有序列表 `TAB + 数字 + . + 空格键`
    2. 项目三的子项目二

### 任务列表（Task lists）

语法：

```
- [ ] 任务一 未做任务 `- + 空格 + [ ]`
- [x] 任务二 已做任务 `- + 空格 + [x]`
```

效果：

- [ ] 任务一 未做任务 `- + 空格 + [ ]`
- [x] 任务二 已做任务 `- + 空格 + [x]`

## 图片

语法：

```
![描述](https://www.google.com.hk/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png)
格式: ![Alt Text](url)
```

效果：

![google](https://www.google.com.hk/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png)

在图片描述后加 `-w + 图片宽度` 即可：

![google-w140](https://www.google.com.hk/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png)

## 链接

语法：

```
email <example@example.com>
[GitHub](http://github.com)
自动生成连接  <http://www.github.com/>
```


效果：

email <example@example.com>
[Github](http://github.com)
自动生成链接： <http://www.github.com/> 

## 区块引用

语法：

```
话题:
> 第一行内容
> 第二行内容
```

效果：

话题:
> 第一行内容
> 第二行内容

## 行内代码

语法：

```
像这样即可：`<addr>` `code`
```

效果：

像这样即可：`<addr>` `code`

## 多行或者一段代码

语法：

    ```js
    function fancyAlert(arg) {
        if(arg) {
        $.facebox({div:'#foo'})
        }
    
    }
    ```

效果：

```js
function fancyAlert(arg) {
    if(arg) {
    $.facebox({div:'#foo'})
    }

}
```

## 顺序图或流程图

语法：

     ```sequence
    用户->服务器: 输入帐号密码登录
    服务器->数据库: 查询数据库
    Note right of 数据库:根据帐号查 找密码
    数据库-->服务器: 返回密码
    Note right of 服务器:比较密码
    服务器-->用户: 密码错误，登录失败。
    ```

    ```flow
    st=>start: 启动应用
    e=>end: 正常使用
    st2=>start: 登录页面
    op1=>operation: 登录
    op2=>operation: 登出
    cond=>condition: 是否登录？
    
    st->cond
    cond(yes)->e
    cond(no)->st2
    e->op2->cond
    st2->op1->cond
    ```

效果：

```sequence
用户->服务器: 输入帐号密码登录
服务器->数据库: 查询数据库
Note right of 数据库:根据帐号查找密码
数据库-->服务器: 返回密码
Note right of 服务器:比较密码
服务器-->用户: 密码错误，登录失败。
```

```flow
st=>start: 启动应用
e=>end: 正常使用
st2=>start: 登录页面
op1=>operation: 登录
op2=>operation: 登出
cond=>condition: 是否登录？

st->cond
cond(yes)->e->op2(right)->cond
cond(no)->st2->op1(right)->cond
```

更多请参考：<http://bramp.github.io/js-sequence-diagrams/>, <http://adrai.github.io/flowchart.js/>

## 表格

语法：

```
第一格表头 | 第二格表头
--------- | -------------
内容单元格 第一列第一格 | 内容单元格第二列第一格
内容单元格 第一列第二格 多加文字 | 内容单元格第二列第二格
```

效果：

第一格表头 | 第二格表头
--------- | -------------
内容单元格 第一列第一格 | 内容单元格第二列第一格
内容单元格 第一列第二格 多加文字 | 内容单元格第二列第二格


## 删除线

语法：

    加删除线像这样用： ~~删除这些~~

效果：

加删除线像这样用： ~~删除这些~~

## 分隔线

以下三种方式都可以生成分隔线：


```
***

*****

- - -
```

效果：

***

*****

- - -



## MathJax

语法：

```
块级公式：
$$	x = \dfrac{-b \pm \sqrt{b^2 - 4ac}}{2a} $$

\\[ \frac{1}{\Bigl(\sqrt{\phi \sqrt{5}}-\phi\Bigr) e^{\frac25 \pi}} =
1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}}
{1+\frac{e^{-8\pi}} {1+\ldots} } } } \\]

行内公式： $\Gamma(n) = (n-1)!\quad\forall n\in\mathbb N$
```

效果：

块级公式：
$$	x = \dfrac{-b \pm \sqrt{b^2 - 4ac}}{2a} $$

\\[ \frac{1}{\Bigl(\sqrt{\phi \sqrt{5}}-\phi\Bigr) e^{\frac25 \pi}} =
1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}}
{1+\frac{e^{-8\pi}} {1+\ldots} } } } \\]


行内公式： $\Gamma(n) = (n-1)!\quad\forall n\in\mathbb N$


## 脚注（Footnote）

语法：

```
这是一个脚注：[^footnotename]
```

效果：

这是一个脚注：[^footnotename]

[^footnotename]: 脚注的具体内容


## 注释和阅读更多

    <!-- comment -->
    <!-- more -->

**注** 阅读更多的功能只用在生成网站或博客时，插入时注意要后空一行。

## TOC

Markdown 语法：

```
[TOC]
```

效果如下：

[TOC]






