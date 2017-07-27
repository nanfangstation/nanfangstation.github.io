---
layout:     post
title:      "Bootstrap-Select用法"
subtitle:   "Bootstrap-select是一个jQuery插件，它使用Bootstrap的dropdown.js样式，并为标准选择元素带来额外的功能。"
date:       2017-07-27
author:     "南方"
header-img: "img/post-bg-bootstrap-select.png"
tags:
    - 前端
    - Bootstrap
---

## 目录
1. [引入依赖](#引入依赖)
2. [html代码](#html代码)
3. [js初始化](#js初始化)
4. [页面效果](#页面效果)
5. [优点](#优点)

---

#### 引入依赖

```js
<!-- Latest compiled and minified CSS -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bootstrap-select/1.12.4/css/bootstrap-select.min.css">

<!-- Latest compiled and minified JavaScript -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/bootstrap-select/1.12.4/js/bootstrap-select.min.js"></script>
```

#### html代码
使用.selectpicker类创建select标签内容。 data-api将自动主题化这些元素。

```html
<div class="col-md-4">
    <label for="path" class="col-sm-4 control-label">访问路径:</label>
    <div class="col-sm-7">
        <select class="form-control selectpicker" style="width: 175px;" name="path" id="path"
                data-live-search="true" title=""></select>
    </div>
</div>
```
#### js初始化

```js
$('.selectpicker').selectpicker({
    size: 10 // 设置下拉框默认大小
  });
```

#### 页面效果
![我是图片](https://raw.githubusercontent.com/nanfangstation/image/master/blog/2017-07/bootstrap-select-demo.png)

#### 优点
1. 支持搜索匹配
2. 长度支持自适应
3. 可设置下拉框大小
4. ...

官网地址：[https://silviomoreto.github.io/bootstrap-select/](https://silviomoreto.github.io/bootstrap-select/)
