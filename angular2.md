# angular2 初识

## Hello world！

1.引入angular预定义类型

``` javascript
    import {Component,View,bootstrap} from "angular2/angular2";
    // import是ES6的关键字，用来从模块中引入类型定义
    //从angular2模块库中引入三个类型：Component类、View类和bootstrap函数
```

2.实现一个angular2组件:定义一个类，然后给这个类添加注解

``` javascript
    @Component({selector:"ez-app"})
    @View({template:"<h1>Hello world!</h1>"})
    class EzApp{}
    /* class 也是ES6的关键字，用来定义一个类。
    * @Component和@View都是给类EzApp附加的元信息，称为注解/Annotation
    * @Component最重要的作用就是通过selector属性（值为CSS选择符），指定这个组件渲染到哪个DOM树上
    * @View最重要的作用是通过template属性，指定渲染的模板
    */
```

3.渲染组件到DOM：需要使用自举/bootstrap函数

``` javascript
    bootstrap(EzApp);
    // 这个函数的作用就是通知angular2框架将EzApp组件渲染到DOM树上
```

### 实例
``` html
    <!doctype html>
    <html>
    <meta charset="utf-8">
    <title>Hello world</title>
    <!-- 模块加载器 -->
    <script type="text/javascript" src="lib/system.js"></script>
    <!-- Angular2模块 -->
    <script type="text/javascript" src="angular2.js"></script>
    <script>
    // 设置模块加载规则
    System.baseURL = document.baseURL;
    System.config({
        map:{traceur:'lib/traceur'},
        traceurOptions:{annotation:true}
    });
    </script>
    <body>
        <!-- 组件渲染锚点 -->
        <my-app></my-app>
        <!-- 定义一个ES6脚本元素 -->
        <script type="module">
        // 从模块库引入三个类型定义
        import {Component,View,bootstrap} from "angular2/angular2";
        // 组件定义
        @Component({selector:"my-app"})
        @View({template:"<h1>Hello world</h1>"})
        class EzApp{}
        // 渲染组件
        bootstrap(EzApp);
        </script>
    </body>
    </html>
```
