# vue_fecshop_appserver

演示地址：http://demo.fancyecommerce.com/

开发状态：【已完成】

做fecshop的前后端彻底分离部分的前端界面部分

1.首先您需要安装npm，详细参看：[安装npm和nodejs](http://www.fancyecommerce.com/2017/07/12/%E5%AE%89%E8%A3%85npm%E5%92%8Cnodejs/)

2.全局安装 vue-cli：  

```
npm install -g vue-cli
```

3.下载本文件

```
git clone https://github.com/fecshop/vue_fecshop_appserver.git
```

4.进入上面下载的文件夹，然后执行。

```
npm install
```

这里需要很长一段时间，您也可以使用淘宝镜像  `cnpm install`

5.下面就可以执行了

开发环境执行

```
npm run dev
```

线上环境执行，

```
npm run build
```


6.文件包里面的文件说明：

`build`: 配置了webpack的基本配置、开发环境配置、生产环境配置

`config`: 中配置了路径端口值等

`node_modules`: 为依赖的模块

`src`: 放置组件和入口文件

`static`: 放置静态资源文件

`index.html`: 文件入口

7.配置

7.1、配置获取远程数据的地址：

开发环境为:`config/dev.env.js`

生产环境为:`config/prod.env.js`

需要更改下面的配置

```
API_ROOT: '"//fecshop.appserver.fancyecommerce.com"', // 数据获取api的地址
WEBSITE_ROOT: '"//demo.fancyecommerce.com"'           // vue客户端访问的首页地址
```

因此，您需要先安装fecshop，并将appserver端配置好，提供api支持，vue才可以通过
api获取数据。

7.2、生产环境设置发布文件地址：

`config/index.js` 文件中的`assetsRoot`为设置生产环境的文件发布地址

```
module.exports = {
  build: {
    env: require('./prod.env'),
    index: path.resolve(__dirname, '../dist/index.html'),
    assetsRoot: path.resolve(__dirname, '../dist'),
```

这个，懂vue的都明白，也就是线上环境编译后文件的存放位置
，因此，在线上环境，您需要将nginx配置的域名指向该文件路径。


7.3、设置开发环境的地址和端口

设置地址：`build/dev-server.js`

```
 var uri = 'http://localhost:' + port
```

设置端口：config/index.js 设置dev里面的port，改为您想要更改的端口

```
port: 8080,
```


7.4、另外，vue里面有一些图片地址，是直接写上的，这个开发者自己替换掉自己的图片地址即可。

7.5、网站的多语言和多货币，是在服务端appserver中进行设置。

8.文档

8.1、[fecshop appserver api 状态码](http://www.fecshop.com/doc/fecshop-guide/develop/cn-1.0/guide-fecshop-server-return-code.html)

8.2、[fecshop appserver的一些说明](http://www.fecshop.com/doc/fecshop-guide/develop/cn-1.0/guide-fecshop-server.html)











