###generator安装方法
1.generator并不随着yeoman安装，需单独安装。安装方法为generator+安装包的名字，比如angular的generator的安装包为`npm install -g generator-angular`
###yeoman
1.更新yeoman的方法`npm install -g yo to update`

2.用yeoman生成项目的方式是yo + 什么项目+项目名称，比如`yo angular +项目名称`，生成angular的项目。

3.生成项目时，需要选择包是，空格代表选择和取消选择。

###bower
1.bower安装文件bower install +名称，比如`bower install jquery`

2.如果没有注册，可以通过githubxie短写安装。

3.如果没有bower.json的话，通过bower init生成。

4.在如果要添加到devdepences,则使用bower install --save-dev

5.增加到生产环境的话 则使用 bower install --save。

6.说到使用script的麻烦

7.在bower中说到了bower生成文件。bower install ,然后是生成bower.json,然后引用script的时候说要结合grunt来说。

###grunt
第一节重点介绍gruntfile.js


###webpack

1-2：讲诉的内容是实战的开始。npm init 创建一个package.jgon。然后就是npm install webpack。然后建立一个hello.js。再用命令webpack hello.js web-hello.js即进行打包。然后再新建一个world.js文件，并在hello.js中引入world.js，并再次进行如上的打包操作。然后在hello.js中通过，通过require，引用style.css。这时出现错误。所以需要安装css-loader。和style-loader。并在require之前加了css-loader。发现正常啦。。在css中加入背景颜色。发现并没有生效。后面发现加上style-loader在require前面就可以了。。在命令中加入--watch。可以监控自动更新。

2-1：讲配置文件webpack.config.js的建立，定义了entry入口文件。出口文件，出口文件名，那就可以通过webpack来运行了。然后可以在package.json中的scrpts中定义，就可以。npm run webpack。并且的话是有配置了其他的参数。

2-2：讲了多口的情况。entry。数组或者对象。用对象的时候。，输出的文件为了区别开来，可以用[name],[hash]。。。对应的文件是test3..

3-1： 出口文件用了hash以后是不一样的。导致在html中指定的麻烦。所以.用html-webpack-plugin去解决。

```javascript
plugins: [
  new htmlWebpackPlugin({
    filename: 'kd.html' //指定名称
    template: 'index.html'//以原本的为模板
    inject: 'body' //值为body,或者head。表示js在body或者head标签中
    data: 'webpack is use ejs语法' //使用ejs语法。<%= htmlWebpackPlugin.options.title %> 
    minify: {
      collapseWhitespace: true //删除html空白
      removeComments: true //删除注释
      minifyJS: true //压缩html文件中<script></script>中的内容。
    }
  })
]
```
ejs语法。如果是表达式的话。要去掉<%=，中的=

3-2： 讲述的内容是，先说ejs语法。然后说如何将一个js文件放在head中另一个js放在body中。。实现代码为
```html
	<script type="text/javascript" src="<%= htmlWebpackPlugin.files.chunks.a.entry %>"></script>

```
然后说如果要上线的话，需要加上域名。实现方式是在output中加入 publicPath:'htttp://cdn.com/',最后讲了压缩的情况，见上

3-3： htmlWebpackPlugin的内容在npmjs.com中可以看到。多页面的情况。复制多一个new htmlWebpackPlugin()。要引入不同的js.可以在chunks中指定。excludechunks。排除的chunks.最后讲优化的东西。我没看了。。最后的代码情况

```javascript
var htmlWebpackPlugin = require('html-webpack-plugin');
module.exports = {
	entry: {
		main: './src/scripts/main.js',
		a: './src/scripts/a.js'
	}, 
	output: {
		path: './dist',
		filename: 'js/[name].js'
	},
	module: {
		loaders: [
			{
				test: /\.css$/,
				loader: 'style-loader!css-loader'
			},
		]
	},
	plugins: [
		new htmlWebpackPlugin({
			filename: 'main.html', // 指定名称
			template: 'index.html', //以原本的为模板
			inject: 'body', //放在head标签还是body标签
			title: 'gongming', //使用ejs语法在html中定义
			chunks: ['main','a'],
			minify: {
				removeComments: true,
				minifyJS: true,
				minifyCSS: true
			}
		}),
		new htmlWebpackPlugin({
			filename: 'a.html', // 指定名称
			template: 'index.html', //以原本的为模板
			inject: 'body', //放在head标签还是body标签
			title: 'gongming', //使用ejs语法在html中定义
			chunks: ['a'],
			minify: {
				removeComments: true,
				minifyJS: true,
				minifyCSS: true
			}
		})
	]
}
```


####第四部分
4-1：对文件进行设置并介绍loader的一些内容


4-2： 介绍babel的情况。并需要制定要转换那个版本的js。指定方式有三个分别是package.json中加babel。在loader下面加query。最后一种是加一个babel文件。可以使用exclud和include。提升速度


4-3: 慕课网webpack视频代码


```javascript
var htmlWebpackPlugin = require('html-webpack-plugin');
var path = require('path');

module.exports = {
	entry: './src/app.js',
	output: {
		path: './dist',
		filename: 'js/[name].bundle.js'
	},
	module: {
		loaders: [
			{
				test: /\.js$/,
				loader: 'babel-loader',
				include: path.resolve(__dirname, 'src'),
				exclude: path.resolve(__dirname, 'node_modules'),
				include: './src/',
				query: {
					presets: ['latest']
				}
			},
			{
				test: /\.html$/,
				loader: 'html-loader'
			},
			{
				test: /\.tpl$/,
				loader: 'ejs-loader'
			},
			{
				test: /\.css$/,
				loader: 'style-loader!css-loader?importLoaders=1!postcss-loader'
			},
			{
				test: /\.styl$/,
				loader: 'style-loader!css-loader!postcss-loader!stylus-loader'
			},
			{
				test: /\.less$/,
				loader: 'style-loader!css-loader!postcss-loader!less-loader'
			},
			{
				test: /\.(png|jpg|gif|svg)$/i,
				loaders:[
					'url-loader?limit=10000&name=assets/[name]-[hash:5].[ext]',
					'image-webpack-loader'
				] 
			}
		]
	},
	plugins: [
		new htmlWebpackPlugin({
			filename: 'index.html',
			template: 'index.html',
			inject: 'body'
		})
	]
}
```
