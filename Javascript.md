![image-20220502232032566](.\笔记素材图\JavaScript-roadmap.png)

![image-20220502232130721](.\笔记素材图\jspart2.png)



## 设置VSCode

```js
// Remember, we're gonna use strict mode in all scripts now!
'use strict';
//所有文件都应该严谨模式
```

### 1 推荐了一个插件，[prettier](https://prettier.io/docs/en/index.html)

### 2 另一个插件 todohighlight

```json
 "todohighlight.isCaseSensitive": true,
  "todohighlight.keywords": [
    {
      "text": "BUG",
      "color": "#333",
      "backgroundColor": "#e74c3c"
    },
    {
      "text": "NOTE",
      "color": "#ff0000",
      "backgroundColor": "yellow",
      "overviewRulerColor": "grey"
    },
    {
      "text": "HACK",
      "color": "#000",
      "isWholeLine": false
    }
  ],
  "todohighlight.include": [
    "**/*.js",
    "**/*.jsx",
    "**/*.ts",
    "**/*.tsx",
    "**/*.html",
    "**/*.php",
    "**/*.css",
    "**/*.scss",
    "**/*.py"
  ]
```

### 3 live serve 插件， 点击golive 按钮

### 4 更专业的自动化 

安装 node  安装`npm install live-server -g`

然后再终端输入  `live-server`





58-62 讲 html与css基础知识





DOM操作

![image-20220507151621577](.\笔记素材图\js定义)

high-level

garbage-collected

interpreted or jsut-in-time compiled

multi-paradigm

prototype-based object-oriented

first-class functions

Dynamic

Single-threaded

non-blocking event loop



## 创建类：

### 扩展类

```js
const EventEmitter = require("events");
const http = require("http");
// const myEmitter = new EventEmitter();

class Sales extends EventEmitter {
    constructor() {
        super();
    }
}
```

## 流：

可读、可写、双工、转换

![image-20220526234125242](.\笔记素材图\4stream.png)

# 导入模块系统解析

![moudle system](.\笔记素材图\module-system.png)

loading

![loading](.\笔记素材图\loadingmoudle.png)

wrapping

![wrapping](.\笔记素材图\wrapping moudle.png)

execution 没得讲，跳过

return

![image-20220527002256850](.\笔记素材图\export moudle.png)

