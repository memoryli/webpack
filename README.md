# webpack

webpack的配置文件
webpack.config.js
const path = require('path')
module.exports = {
  mode: 'production'
  entry: './index.js',
  output: {
    filename: 'index.js', //打包后的文件名字
    path: path.resolve(_dirname, 'dist') // 放在哪个文件夹，绝对路径 _dirname是指webpack所在的当前的目录的路径
  }
}

Loader是什么？
loader的执行顺序是从下到上，从右到左
1、url-loader 把图片变成base64的，不会生成图片，会将其打包进js中，这有一个弊端，当图片较大时，会使得js文件也很大，
可以
`
 options: {
    limit: 204800 //限制200Kb等
  
 }
`
1、css-loader 可以帮我分析出几个css文件之间的关系，合并成一个css文件  importLoader是 执行css-loader的时候，还要执行后面几个loader
2、style-loader 在得到生成的css文件后，会将其挂在到header当中
3、scss-loader 将scss编译成css
4、postcss-loader 添加前缀 -webkit- -m-等 autoprefixer这个插件
5、file-loader 可以用于字体

plugin
html-webpack-plugin 会在打包结束后，自动生成一个html文件，并且会把打包生成的js自动引入html中







