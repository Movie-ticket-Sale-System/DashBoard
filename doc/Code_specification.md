## 前端代码规范

### JavaScript规范

**1.单行注释**

必须独占一行。`//` 后跟一个空格，缩进与下一行被注释说明的代码一致。

**2.多行注释**

避免使用 `/*...*/` 这样的多行注释。有多行注释内容时，使用多个单行注释。

**3.函数/方法注释**

- 函数/方法注释必须包含函数说明，有参数和返回值时必须使用注释标识；
- 参数和返回值注释必须包含类型信息和说明；
- 当函数是内部函数，外部不可访问时，可以使用 @inner 标识；

```
/**
 * 函数描述
 *
 * @param {string} p1 参数1的说明
 * @param {string} p2 参数2的说明，比较长
 *     那就换行了.
 * @param {number=} p3 参数3的说明（可选）
 * @return {Object} 返回值描述
 */
function foo(p1, p2, p3) {
    var p3 = p3 || 10;
    return {
        p1: p1,
        p2: p2,
        p3: p3
    };
}
```

**4.文件注释**

文件注释用于告诉不熟悉这段代码的读者这个文件中包含哪些东西。应该提供文件的大体内容，它的作者，依赖关系和兼容性信息。如下:

```
/**
 * @fileoverview Description of file, its uses and information
 * about its dependencies.
 * @author user@meizu.com (Firstname Lastname)
 * Copyright 2009 Meizu Inc. All Rights Reserved.
 */
```

**5.变量，使用 Camel 命名法**

```
var loadingModules = {};
```

**6.私有属性、变量和方法以下划线 _ 开头**

```
var _privateMethod = {};
```

**7.常量，使用全部字母大写，单词间下划线分隔的命名方式**

```
var HTML_ENTITY = {};
```

**函数**，使用 Camel 命名法。

函数的**参数**，使用 Camel 命名法。

```
function stringFormat(source) {}

function hear(theBells) {}
```

类，使用 Pascal 命名法

类的 方法/属性，使用 Camel 命名法

```
function TextNode(value, engine) {
    this.value = value;
    this.engine = engine;
}

TextNode.prototype.clone = function () {
    return this;
};
```

**8.命名语法**

**类名**，使用名词。

```
function Engine(options) {}
```

**函数名**，使用动宾短语。

```
function getStyle(element) {}
```

**boolean** 类型的变量使用 is 或 has 开头。

```
var isReady = false;
var hasMoreCommands = false;
```

**Promise** 对象用动宾短语的进行时表达。

```
var loadingData = ajax.get('url');
loadingData.then(callback);
```

**9.使用空格代替tab进行缩进**

使用两个空格代替tab键，对代码进行缩进管理。

**10.杜绝var**

使用const或let来声明所有局部变量。如果变量不需要被重新赋值，默认应该使用const。

**11.使用模板字符串取代连接字符串**

在处理多行字符串时，使用模板字符串代替+号连接字符串

**12.使用单引号**

只允许使用单引号包裹普通字符串，禁止使用双引号。

### 项目文件规范

**1.文件命名由多个单词组成，采用中划线连接**

**2.文件名称只由小写英文字母、数字、中划线组成，不应包含特殊符号**

**3.每个页面的默认入口文件应当命名为index.vue**

**4.公共组件统一放置在components文件夹中；页面组件统一放置在pages文件夹中，每个页面的文件夹命名参考文件命名规则**

**5.父组件与子组件间应当以目录结构的方式表现出层级关系，如子组件放置在childrens文件夹中，且childrens文件夹与父组件放置在同一目录下**

## 后端代码规范

**1.1、命名总规则**

- 所有名称的字符范围为：A-Z, a-z, 0-9 和_(下划线)。不建议使用其他字符作为名称。
- 采用英文单词或英文短语（包括缩写）作为名称，不使用无意义的字符或汉语拼音。
- 名称应该清晰明了，能够准确表达事物的含义，最好可读，遵循“见名知意”的原则。
- 提倡英文命名，切忌英文和拼音混用。

**1.2、类库Namespace命名**

类库分成三个层次，分别是.Net框架、公司基础公共类库、项目级类库。公共类库参照已有类库引用，以下主要对项目级Namespace命名提出参考建议：

YesHJ.Ucenter 用户中心
YesHJ.Cms 网站内容系统
YesHJ.Class 网校
YesHJ.Bulo 社区
YesHJ.Shop 网店
命名空间建议： YesHJ.{ProductLine}.{Appname}.XXXX =>例如：YesHJ.Bulo.KaoDian.XXXX

**1.3、变量、方法命名**

- 私有变量及方法参数使用camel命名（第一个词首字母用小写，其它词首字母用大写）
- 公共变量、方法、类使用Pascal命名（单词的首字母用大写）
- 公有变量尽量使用Property ，慎用Public Static变量；
- 变量命名要有意义：拒绝无意义的变量a，a1，b，k等；
- 典型的增删改查方法命名如下：比如获取GetUserList
- 用名词或名词短语命名属性；

**1.4、文件、文件夹命名**

- 目录命名建议和Class命名要求一致，不要出现“_”和“小写”开头，已经用小写的不需要调整，保证命名空间的命名符合标准即可。
- 特殊或者系统文件夹可保持大写方式，比如App_Code、App_WebReferences等；
- 文件命名一般采用小写，应用加下划线方式命名。
- 页面的命名和Class命名要求一致，注意不要小写开头。

### 【Web服务】

**1.URL命名：**

老的Api方式：app.hujiang.com.hjdns.net => {appName}.hjapi.hujiang.com (内部域名解析) 还有一些是使用 {appName}.yeshj.com

**2.传参：不要暴露参数类型和参数值**

不好的例子：
<http://bulo.hujiang.com/service/GetUserFace.ashx?ver=2013%E5%B9%B44%E6%9C%8816%E6%97%A5%20>%E4%B8%8B%E5%8D%885:07:52&userId=12644342&callback=jQuery17207177500906400383_136610325 2485&_=1366103272413

应该是：
<http://bulo.hujiang.com/service/GetUserFace.ashx?token=asdfkjsldjwlejfsldjflsdjlf&callback=jQuery17207177500906400383_1366103252485&_=1366103272413>

**3.类型和应用场景：**

- Web Service：传统用法，不宜调用太频繁。注意要有异常保护，即使不返回结果，也不要影响页面的其他功能，尽量用异步。
- Rest Service：一般参数要保护；同样不宜调用太频繁。尽量用Json做数据格式。
- WCF Service：适用于高安全、频繁调用，同时不能直接产生数据库关联的场景。

### 【代码风格】

**2.1、代码前置后置**

代码前后端分离：(code-behind)
好处，逻辑比较清晰，容易进行重构。
缺点：发布、维护繁琐一些。

今后新项目必须采用代码后置(code-behind)，不要再使用单页面（single-page code ），特别是UserControl等需要复用的，自己在维护代码时，修改单页面程序时，要把它改成code-behind。

建议：

1. 需要简化前台代码的数量和复杂度，必要时需要分离出独立的Service层，前端的C#代码仅仅用来做交互性的操作，不要包含太多复杂逻辑。
2. 新项目尽量采用Web Application Project，不建议使用Web Site Project。

**2.2、注释**

- 逻辑理解注释，采用//加注释语句
- 写在注释语句之前一行或者紧跟着注释语句后同一行
- public,protect函数或者属性注释采用/// VS自动添加注释模式，
- 所有共有变量和共有方法都需要注释，类库中的protect和public的类要加类头注释

**2.3、书写格式**

- 在程序代码间一般不要连续留空两行
- 如果一个函数的参数很多，要么一行全部输入，要么一行一个参数
- 不要用空格缩进，统一用制表符缩进
- 对于一些比较长的块，使用#region 和#endregion 来括起来
- 单行代码要 < 80个字符
- C#代码中的SQL要排版，方便阅读和维护；格式：参照数据库开发规范。