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

1-2：讲诉的内容是实战的开始。npm init 创建一个package.jgon。然后就是npm install webpack。然后建立一个hello.js。再用命令webpack hello.js web-hello.js即进行打包。然后再新建一个world.js文件，并在hello.js中引入world.js，并再次进行如上的打包操作。然后在hello.js中通过，通过require，引用style.css。这时出现错误。所以需要安装css-loader。和style-loader。并在require之前加了css-loader。发现正常啦。
