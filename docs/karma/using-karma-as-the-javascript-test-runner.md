# 使用 Karma 运行 JavaScript 测试

http://icodeit.org/2013/10/using-karma-as-the-javascript-test-runner/

Oct 8th, 2013

Karma是一个JavaScript的测试运行器。事实上，Karma更是一个测试环境，使用Karma可以很方便的的运行测试(方便到你感觉不到它的实际存在)。

一般的TDD的开发流程为：

1. 编写测试(一个会失败的case)
2. 运行测试，并看到这个测试失败
3. 编写代码(足够让测试通过的代码)
4. 运行测试，并看到测试通过
5. 重构
6. 运行测试，并看到测试通过

然后如此循环，而在前端开发中，很长一段时间，这个流程受限于开发环境，比如添加了一个新的JavaScript源文件，开发者需要在HTML中引入相应文件，以及相应测试文件，然后刷新页面(有时候还需要清空浏览器缓存)。

在这个过程中，开发者真正关注的就是编写测试，运行测试，编写实现，重构等等，需要不断的重复这个过程。而不是关注如刷新页面，清空缓存，修改HTML对脚本的引用等无关的工作。

Karma就是这样一个开发环境，开发者指定需要测试的脚本/测试文件，需要运行的浏览器等信息，Karma会在后台自动监控文件的修改，并启动一个浏览器与Karma的服务器连接，这样当源代码或者测试发生修改后，Karma会自动运行测试。

开发者可以指定不同的浏览器，甚至可以跨设备。由于Karma只是一个运行器，你可以使用项目中正在使用的测试框架如Jasmine，QUnit等，甚至可以自定义适配器来支持你自己的测试框架。

## 运行 Karma

Karma 需要一个配置文件来知道哪些文件需要被加载，需要被监控(当文件内容发生变化时，尝试运行测试)，这个配置文件可以通过 Karma 自带的参数来生成。

### 基本使用

安装

```
$ npm install -g karma
```

生成配置文件

```
$ karma init my.conf.js
```

karma 会让你回答一些问题，比如是哪种测试框架，哪些文件需要被测试，哪些浏览器需要被考虑等。生成的配置文件的一个片段是：

```javascript
basePath = '';

files = [
    JASMINE,
    JASMINE_ADAPTER,
    'src/**/*.js',
    'test/**/*spec.js'
];

port = 9876;

browsers = ['Chrome'];
```

生成配置文件之后，可以通过命令来启动Karma服务器，同时指定使用my.conf.js文件作为配置：

```
$ karma start my.conf.js
```
