**gulp**



自动化构建工具（fis3、gulp、grunt）

使用：<http://www.ydcss.com/archives/18>

gulp是基于Nodejs的自动任务运行器， 她能自动化地完成 javascript/coffee/sass/less/html/image/css 等文件的的测试、检查、合并、压缩、格式化、浏览器自动刷新、部署文件生成，并监听文件在改动后重复指定的这些步骤。

使用流程：

​    安装nodejs -> 全局安装gulp -> 项目安装gulp以及gulp插件 -> 配置gulpfile.js -> 运行任务



\1. 安装 nodejs

node -v

npm -v



使用 npm 安装包：node package manager

npm install <package-name> -g （--save-dev）



-g 全局安装

--save 局部安装并保存到package.json配置中

-dev  存在package.json的devDependencies配置项里，意思是生产环境依赖的模块



文件：package.json(NodeJS项目的配置文件)





选择性安装 cnpm （<http://npm.taobao.org/>）:

npm install -g cnpm --registry=[https://registry.npm.taobao.org](https://registry.npm.taobao.org/)

可以使用 cnpm 替代 npm 来安装资源







\2. 全局安装 gulp

npm install gulp@3 -g

或：

cnpm install gulp@3 -g

测试：gulp -v



以下步骤在项目目录下操作：



\3. 在项目目录下生成 package.json 文件：

npm init -y

或

cnpm init -y



\4. 在项目目录中本地安装 gulp：

cnpm install gulp --save-dev

本地安装成功后，会生成 node_modules 文件夹



\5. 在项目目录中本地安装 gulp 插件([https://www.npmjs.com](https://www.npmjs.com/))：



压缩CSS：gulp-clean-css

npm install gulp-clean-css --save-dev



压缩JS：gulp-uglify

cnpm install --save-dev gulp-uglify



压缩Html：gulp-htmlmin

cnpm install --save-dev gulp-htmlmin







**gulpfile.js**



const gulp = require('gulp');

const cleanCss = require('gulp-clean-css');

const uglify = require('gulp-uglify');

const babel = require('gulp-babel');

const htmlmin = require('gulp-htmlmin');



gulp.task('default', function() {

​    // 将你的默认的任务代码放在这

​    console.log('gulp启动成功');

});



gulp.task("hello", function(){

​    console.log("hello gulp");

});



gulp.task("html", function(){

​    gulp.src("src/index.html")

​        .pipe(htmlmin({

​               removeComments: true,//清除HTML注释

​               collapseWhitespace: true,//压缩HTML

​               collapseBooleanAttributes: true,//省略布尔属性的值 <input checked="true"/> ==> <input />

​               removeEmptyAttributes: true,//删除所有空格作属性值 <input id="" /> ==> <input />

​               removeScriptTypeAttributes: true,//删除<script>的type="text/javascript"

​               removeStyleLinkTypeAttributes: true,//删除<style>和<link>的type="text/css"

​               minifyJS: true,//压缩页面JS

​               minifyCSS: true//压缩页面CSS 

​           })

​        )

​        .pipe(gulp.dest("dist"))

});



gulp.task("css", function(){

​    gulp.src("src/css/*.css")

​        .pipe(cleanCss())

​        .pipe(gulp.dest("dist/css"));

});



gulp.task("js", function(){

​    gulp.src("src/js/*.js")

​    .pipe(uglify())

​    .pipe(gulp.dest("dist/js"));

});









将ES6转换为ES5：gulp-babel



cnpm install --save-dev gulp-babel @babel/core @babel/preset-env



gulpfile.js中修改js任务

var babel **=** require('gulp-babel');

gulp.task('js', function(){

​    gulp.src('src/**/*.js')

​    .pipe(babel({

​        presets**:** ['@babel/env']

​    }))

​    .pipe(uglify())

​    .pipe(gulp.dest('dist/js'))

});









服务器：gulp-connect



cnpm install --save-dev gulp-connect



gulpfile.js中新增代码



var connect = require('gulp-connect');



gulp.task('server', function() {

​    connect.server({

​        livereload: true,

​        port: 2333

​    });

});





文件合并



cnpm install --save-dev gulp-concat





gulpfile.js中修改js任务

var concat = require("gulp-concat");

gulp.task("js", function(){

​    gulp.src("src/js/**/*.js")

 .pipe(babel({

   presets**:** ['@babel/env']

 }))

​    .pipe(concat('all.js'))

​    .pipe(uglify())

​    .pipe(gulp.dest("dist/js"))

​    .pipe(connect.reload());

});







watch：监听文件的的变化执行对应的任务



给每一个任务加上pipe(connect.reload())



gulp.task('watch',function(){

​    gulp.watch('./src/css/*.scss',['sass']);

​    gulp.watch('./src/*.html',['html']);

​    gulp.watch('./src/css/*.css',['css']);

​    gulp.watch('./src/js/*.js',['js']);

})



gulp.task("default", ["sass", "html", "js", "connect", "watch"]);







处理图片





gulp.task("img", function(){

​    gulp.src('src/images/**/*')

​    .pipe(gulp.dest('dist/images'))

})

gulp.task("default", ["sass", "html", "minijs", "connect", "watch", "img"]);













sass转css  gulp-sass



npm install node-sass gulp-sass --save-dev



var sass = require('gulp-sass');



gulp.task('sass', function(){

​    gulp.src('src/css/*.scss')

​    .pipe(sass())

​    .pipe(gulp.dest('dist/css'))

});

邮箱
npm install nodemailer --save
express框架
npm install express --save
body parser 
npm install --save body-parser
安装库
npm i mongoose --save
apidoc生成接口文档
npm install apidoc -g
安装session与cookie 一样进行保存相关的信息 这个sestion 是记录每一个用户独有的id
npm i express-session
解决跨域的方式  用npm 直接一步解决
npm i cors -save
实现上传功能
lnstallation
npm i --save multer
npm i --save axios
