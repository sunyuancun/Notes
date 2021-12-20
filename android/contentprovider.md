# ContentProvider

* **URI**&#x20;

&#x20;   ****    统一资源标识符,

&#x20;  作用：唯一标识 ContentProvider & 其中的数据

```
外界进程通过 URI 找到对应的ContentProvider & 其中的数据，再进行数据操作
```

![](../.gitbook/assets/企业微信截图\_20211220104239.png)

```
// Some code
// 设置URI 
Uri uri = Uri.parse("content://com.carson.provider/User/1")
// 上述URI指向的资源是：名为 `com.carson.provider`的`ContentProvider` 中表名 为 `User` 中的 `id`为1的数据

// 特别注意：URI模式存在匹配通配符* & ＃

// *：匹配任意长度的任何有效字符的字符串
// 以下的URI 表示 匹配provider的任何内容
content://com.example.app.provider/*

// ＃：匹配任意长度的数字字符的字符串
// 以下的URI 表示 匹配provider中的table表的所有行
content://com.example.app.provider/table/#

```

* **MIME数据类型**

&#x20;  ****   MIME类型就是设定某种扩展名的文件用一种应用程序来打开的方式类型，当该扩展 名文件被访问的时候，浏览器会自动使用指定应用程序来打开。多用于指定一些客户端自定义的 文件名，以及一些媒体文件打开方式。

ContentProvider根据 URI 返回MIME类型

```
ContentProvider.geType(uri);//return String
```

MIME类型组成,每种 MIME 类型 由2部分组成 = **类型 + 子类型**

```
// MIME类型是 一个 包含2部分的字符串
text / html  text/css   application/pdf
```

* **ContentProvider类**

ContentProvider主要以表格的形式组织数据,同时也支持文件数据，只是表格形式用得比较多

进程间共享数据的本质是：添加、删除、获取 & 修改（更新）数据

![](../.gitbook/assets/企业微信截图\_20211220110207.png)

* **ContentResolver类**

统一管理不同 ContentProvider 间的操作

1. 通过 URI 即可操作 不同的 ContentProvider 中的数据&#x20;
2. 外部进程通过 ContentResolver 类 从而与 ContentProvider 类进行交互

为什么要使用通过 ContentResolver 类从而与 ContentProvider 类进行交互，而不直接访 问 ContentProvider 类？

1. 一款应用要使用多个 ContentProvider ，若需要了解每个 ContentProvider 的不 同实现从而再完成数据交互，操作成本高 & 难度大
2. 一个 ContentResolver 类对所有 的 ContentProvider 进行统一管理

使用示例

![](../.gitbook/assets/企业微信截图\_20211220112555.png)

辅助操作 ContentProvider 的工具类

ContentUris

![](../.gitbook/assets/企业微信截图\_20211220112906.png)

UriMatcher

![](../.gitbook/assets/企业微信截图\_20211220113120.png)

![](broken-reference) ![](<../.gitbook/assets/企业微信截图\_20211220113132 (1).png>)

ContentObserver

![](../.gitbook/assets/企业微信截图\_20211220113338.png)

