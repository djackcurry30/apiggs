# 🐷 Apiggs - 非侵入的RestDoc文档生成工具

![](https://img.shields.io/badge/language-java-yellow.svg)
![](https://img.shields.io/badge/build-processing-green.svg)
[ ![Download](https://api.bintray.com/packages/apiggs/maven/apiggs/images/download.svg) ](https://bintray.com/apiggs/maven/apiggs/_latestVersion)

### 前言
程序员一直以来都有一个烦恼，只想写代码，不想写文档。代码就表达了我的思想和灵魂。

Python提出了一个方案，叫**docstring**，来试图解决这个问题。即编写代码，同时也能写出文档，保持代码和文档的一致。docstring说白了就是一堆代码中的注释。Python的docstring可以通过help函数直接输出一份有格式的文档，本工具的思想与此类似。


### 代码即文档

Apiggs是一个**非侵入**的RestDoc文档生成工具。工具通过分析代码和注释，获取文档信息，生成RestDoc文档。

### 引入插件

* [apiggs-gradle-plugin](https://github.com/apiggs/apiggs-gradle-plugin) **free**
* [apiggs-maven-plugin](https://github.com/apiggs/apiggs-maven-plugin) **free**
* [apiggs-idea-plugin](https://github.com/apiggs/apiggs-idea-plugin)

### 有这样一段代码

```java
/**
 * Building a RESTful Web Service
 * 来自spring的官方示例:https://spring.io/guides/gs/rest-service/
 */
@RestController
public class GreetingController {

    private static final String template = "Hello, %s!";
    private final AtomicLong counter = new AtomicLong();

    /**
     * Web Endpoint greeting
     * @param name who is this
     * @return
     */
    @RequestMapping("/greeting")
    public Greeting greeting(@RequestParam(value="name", defaultValue="World") String name) {
        return new Greeting(counter.incrementAndGet(),
                String.format(template, name));
    }
}
```

### 运行插件

* gradle 运行 task: 
```
Tasks/documentation/apiggs
```
* maven 运行 
```
compile
```


### 生成文档
在编译目录下生成apiggs文件夹，并生成三个文件：
1. .json文件，可直接导入postman
1. .adoc文件，Asciidoc源文件
1. .html文件，源文件渲染结果，效果如下图

![example](https://apiggy-1252473972.cos.ap-shanghai.myqcloud.com/greeting.jpg)

### Versions

#### 1.1
* 增加注释Tag @return的支持，只支持类的全限定名
* 插件支持子项目解析

#### 1.0
* 解析spring mvc源代码，构建Restful Api树
* 生成postman v2.1格式的json文件
* 生成Asciidoc文件
* 渲染Asciidoc文件，生成html文件
* 支持泛型的参数
* 自定义注释Tag @index，定义文档顺序

