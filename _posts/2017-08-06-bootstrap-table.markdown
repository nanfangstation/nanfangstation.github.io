---
layout:     post
title:      "Bootstrap-Table"
subtitle:   "Bootstrap Table的简单使用。"
date:       2017-08-06
author:     "南方"
header-img: "img/post-bg-bootstrap-table.jpg"
catalog: true
tags:
    - Bootstrap
    - 前端
---

#### 简介
基于 Bootstrap 的 jQuery 表格插件，通过简单的设置，就可以拥有强大的单选、多选、排序、分页，以及编辑、导出、过滤（扩展）等等的功能。

官网地址：[http://bootstrap-table.wenzhixin.net.cn/zh-cn/](http://bootstrap-table.wenzhixin.net.cn/zh-cn/)

Github地址：[https://github.com/wenzhixin/bootstrap-table](https://github.com/wenzhixin/bootstrap-table)

导出插件：[tableExport.jquery.plugin](https://github.com/hhurz/tableExport.jquery.plugin)

#### 下载
Bootstrap table (当前版本 v1.11.1) 可以有几种快速入门的方法。

###### 1. 源码
包含了 css，JavaScript，多语言和扩展，以及文档。

[下载源码](http://bootstrap-table.wenzhixin.net.cn/zh-cn/getting-started/
bootstrap-table)

###### 2. 克隆或者 Fork 通过 GitHub

[通过github](https://github.com/wenzhixin/bootstrap-table)

###### 3. CDN
CDNJS 或者 bootcss 提供了 CDN 来支持 Bootstrap table 的 CSS 和 JavaScript 文件链接。

```
<!-- Latest compiled and minified CSS -->
<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/bootstrap-table/1.11.1/bootstrap-table.min.css">

<!-- Latest compiled and minified JavaScript -->
<script src="//cdnjs.cloudflare.com/ajax/libs/bootstrap-table/1.11.1/bootstrap-table.min.js"></script>

<!-- Latest compiled and minified Locales -->
<script src="//cdnjs.cloudflare.com/ajax/libs/bootstrap-table/1.11.1/locale/bootstrap-table-zh-CN.min.js"></script>
```

#### 使用
###### 1. 引入样式
```
<link href="https://cdn.bootcss.com/bootstrap-table/1.11.1/bootstrap-table.min.css" rel="stylesheet">
```

###### 2. 引入js
```
<script src="https://cdn.bootcss.com/bootstrap-table/1.11.1/bootstrap-table.min.js"></script>
<script src="https://cdn.bootcss.com/bootstrap-table/1.11.1/locale/bootstrap-table-zh-CN.min.js"></script>
<script src="https://cdn.bootcss.com/bootstrap-table/1.11.1/extensions/export/bootstrap-table-export.min.js"></script>
<script src="http://rawgit.com/hhurz/tableExport.jquery.plugin/master/tableExport.js"></script>
```

通过 data 属性或者 JavaScript 来启用 Bootstrap Table 插件，显示丰富的功能。

###### 3. 通过 data 属性的方式
```
<div id="toolbar" class="btn-group">
    // 图表切换选项
    <select id="table_switch" class="form-control" name="table_switch"
            required="required" style="width: 80px;">
        <option value="表格" selected>表格</option>
        <option value="柱状图">柱状图</option>
    </select>
    // 下载配置选项
    <select class="form-control">
        <option value="">下载本页</option>
        <option value="all">下载所有</option>
        <option value="selected">下载所选</option>
    </select>
</div>
<table id="table"
       data-search="true" //是否允许搜索
       data-toolbar="#toolbar"
       data-show-refresh="true" //是否刷新
       data-show-columns="true"
       data-pagination="true" //是否分页
       data-height="250" 
       data-show-export="true"  //是否显示导出
       data-striped="true"
       data-show-pagination-switch="true"
       data-strictSearch="true"
       data-showToggle="true"
       data-sort-order="desc"
       data-sort-stable="true"
       data-click-to-select="true"
       data-toolbar="#toolbar"
       data-toggle="table"
       data-checkbox="true"
       data-show-toggle="true"
       data-page-list="[10, 25, 50, 100, ALL]">
    <thead>
    <tr>
        <th data-field="state" data-checkbox="true"></th>
        <th data-field="system">监控系统</th>
        <th data-field="servicePath">访问路径</th>
        <th data-field="serviceName">访问路径名称</th>
        <th data-field="invoker">调用方</th>
        <th data-field="invokerName">调用方名称</th>
        <th data-field="count" data-sortable="true">调用次数</th>
        <th data-field="percent" data-sortable="true">占比(%)</th>
    </tr>
    </thead>
</table>
```

###### 4. 通过 JavaScript 的方式
```
// 初始化
$('#table').bootstrapTable({
  data: tableData,
  height: '600px',
  exportOptions: {  // 导出参数配置
    fileName: fileName,  // 导出文件名称配置
    ignoreColumn: [0]  // 导出忽略第一列
  }
});
// 下载初始化
$(function () {
  var $table = $('#table');
  $(function () {
    $('#toolbar').find('select').change(function () {
      $table.bootstrapTable('refreshOptions', {
        exportDataType: $(this).val()
      });
    });
  })
});
```

#### 效果

![](https://raw.githubusercontent.com/nanfangstation/image/master/blog/2017-08/bootstrap-table-demo.png)

#### 优点

* 界面采用扁平化的风格，用户体验比较好，更好兼容各种客户端
* 配置简单，文档齐全
* 开源、免费
