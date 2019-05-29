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
clean-webpack-plugin 清除dist再重新打包
SourceMap配置
他是一个映射关系，能映射出源代码的错误位置，不过打包会变慢
devtool：‘sourceMap’
inline-source-map 会把.map文件打包到目标js文件中
cheap-inline-source-map 只告诉第几行，不告诉第几列,性能会提升
module  不光业务代码的错误，还包括第三方库
eval 性能最好，但是复杂的业务代码不太好定位
cheap-module-eval-source-map  devlpoment
cheap-module-source-map   production
 WebpackDevServer来提升开发效率
 自动打包，自动刷新浏览器
 devServer：{
  contentBase: './dist',
  open: true  //自动打开一个浏览器
 }
 Hot Module Replacement 热模块更新
 HotModuleReplacementPlugin，他是webpack的一个插件,当css的文件发生改变的时候，只会替换css的内容，html内容不会被改变
devServer：{
  contentBase: './dist',
  open: true,  //自动打开一个浏览器
  hot: true,
  hotOnly: true
 }
plugin：[
  new webpack.HotModuleReplacementPlugin()
]

if(module.hot) {
  module.hot.accept('./number',() => {
    number()
  })
}


Tree Shaking 概念详解 摇树优化
只支持ES Module

Develoment 和 Production 模式的区分打包

Webpack 和 Code Splitting 代码分割
1、同步代码：webpack.common.js中做optimisition的配置即可
2、异步代码（impoort），无须配置，会自动进行代码分割








