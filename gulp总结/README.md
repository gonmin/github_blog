#gulp总结
###常用的gulp模块
1.gulp-uglify  压缩javascript代码

2.gulp-minify-css 压缩css

3.gulp.spritsmith 压缩图片做成轮播图

4.gulp-concat 合并文件

5.gulp-rename 重命名

6.gulp-watch-path 监控文件
###js压缩
1.**gulp的安装**，使用`npm install gulp -g`将gulp安装到全局

2.安装gulp和压缩需要的gulp-uglify,国内的情况下，使用淘宝的cnpm install gulp 和cnpm install gulp-uglify

3.在根目录下建gulpfile.js文件，以下为gulpfile.js文件中的内容

```javascript
//引入上述两个模块
var gulp = require('gulp');
var uglify = require('gulp-uglify');
//接着开始写task
gulp.task('firstScript',function(){
  gulp.src('script/*.js')
      .pipe(uglify())
      .pipe(gulp.dest('newScript'));
};
```
4.在工作目录安装gulp  `npm install --save-dev gulp`
