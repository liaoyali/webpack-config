### webpack 4 的基本配置
遇到的主要是由于版本变化而导致的问题，主要遇到的问题有：
#### 1）
 报错：Error: Cannot find module '@babel/core'
 解决方法：这是由于babel-loader8.x报错，需要安装最新版babel配套插件
  module.exports = {
     presets: ['@babel/preset-env'],
      plugins: ['@babel/plugin-transform-runtime', '@babel/plugin-proposal-  class-properties']
 }
 #### 2）
 报错：You may need an appropriate loader to handle this file type."
 解决方法：这是由于vue-loader15.x新版本带来的问题，需要添加一个plugin到 webpack的配置文件const VueLoaderPlugin = require('vue-loader/lib/  plugin')，然后在plugins数组中实例化new VueLoaderPlugin()
 #### 3）
 报错：GET http://localhost:3000/[object%20Module] 404 (Not Found)
 解决方法：这是由于file-loader在新版本中默认采用ES模块语法，而vue生产的是common.js语法，所以可以在options中加esModule:false。