# 开坑记录一些平时遇到的问题和知识点
1、前端模块化

- 命名空间
  Jquery：window.$
- Common js 
  node.js采用的方案
  require同步引入一个模块化，module.exports导出一个模块
  无法直接运行在浏览器环境下，需要通过工具转换成标准的ES5
- AMD
  通过异步的方式引入一个模块，amd规范主要用于解决针对浏览器环境的模块化问题
  代表require.js，可并行加在多个依赖
  浏览器环境并不原生支持，需要导入实现了AMD的类库
- ES6模块化
  终极模块化方案，浏览器和node.js都以此为目标
  逐渐取代common.js和amd，成为浏览器和服务器通用的模块解决方案
  Import & export
  目前无法直接运行在大部分浏览器环境下，需要工具转换成es5
- 样式文件的模块化
  scss，@import语句

2、 新语言

- es6
  
- typescript
  typescript是js的超集，除了支持es6的全部功能，还提供静态类型检查
  适用于大型项目，在编译阶段就可以找出可能存在的问题
- flow
  与typescript相似但是更加灵活。
  可以只在有需要的地方加上类型检查

3、构建的目的

	新框架、新语言带来各种便利的同时，几乎无法直接运行，需要转换

    构建包括：

- 代码转换
- 文件优化
- 代码分割
- 模块合并
- 自动刷新
- 代码校验
- 自动发布
  构建其实是工程化、自动化思想在前端开发中的体现，将一系列流程用代码去实现，让代码自动去执行这一系列复杂的流程，解放生产力
  
  - 构建工具——大多数构建工具都是用Node.js开发的
  - npm script
    npm是安装node.js时附带的包管理器，npm script是npm内置的一个功能
    允许在package.js文件中使用script字段定义任务，
    script字段是一个对象，每一个属性对应一段shell脚qq
  - grunt
  - gulp
  - fis3
  - webpack
  - Rollup 





4、webpack

- loader
  Loader 可以看做具有文件转换功能的翻译员，modules.rules配置了一组规则，告诉webpack在遇到哪些文件时使用哪些loader去加载和转换
  - Css-loader & style-loader
    Css-loader读取css文件，style-loader将css内容注入到js中
    style-loader工作原理
    将css的内容以字符串的方式存储到javascript中，在网页执行js时通过dom操作，动态的向html head标签离插入html style标签。
     缺点：让js变大，并且加载网页的时间变长
    也可以将css文件单独抽取出来
    除了在webpack配置文件中使用loader，还可以在代码源码中指定用什么Loader去处理文件
    
    
  - Pos
- plugin
  通过在构建流程中注入钩子实现
- devserver
  - devserver会将webpack构建出的文件保存在内存中，访问需要通过http服务访问，
  - Devserver不会理会config中的output数属性，所以要获取入口加载的js,正确的路径是
    http://localhost:8080/bundle.js
- webpack执行过程浅析
  - wp在启动后会从Entry里配置的module开始，递归解析Entry依赖的所有module
  - 每找到一个module，就会根据配置的loader 进行转换，以此递归，找出所有模块
  - 这次模块会以一个entry为一组，一个entry中所有的模块会被打包成一个chunk输出
  - 最后将所有的chunk输出
  - wp会在适当的时机执行plugin里的逻辑

配置详解

总览：

!1543375535434](../img/1543375535434.jpg)



配置文件不止返回一个object，还可以返回其他形式

- entry
  类型：string，array，obj
  ![1543392278214](/Users/didi/Desktop/doc/1543392278214.jpg
  
  library,libraryTarget,externals的区别及作用
  https://juejin.im/post/5b19df3c6fb9a01e643e25d7
- context
  webpack在寻找配置文件中的相对路径时，会以context为根目录，context配置的路径必须是绝对路径
- output
  output是一个对象
  - filename
  webpack中的hash、chunkhash、contenthash区别：https://juejin.im/post/5a4502be6fb9a0450d1162ed 
  
- 
  webpack在寻找配置文件中的相对路径时，会以context为根目录，context配置的路径必须是绝对路径
  	
  
  























 




