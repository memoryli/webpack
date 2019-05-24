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





