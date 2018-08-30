Vue.js CLI
==============

簡單來說它是 Vue.js 官方提供的開發工具，可用於快速開發大型單頁應用程式 (SPA)，更具體來說像是前端在開發時，常會搭配一些前端管理工具 (Gulp、Webpack...) 來處理瑣碎又重複性的工作，但往往需要大量時間去自行配置開發環境，而 Vue-cli 就像開發懶人包，可透過指令快速地建立一個立即可用的 Vue 開發環境。

## 提供樣板

* webpack
* webpack-simple
* browserify
* browserify-simple
* pwa
* simple

## Step 1. 安裝 Node.js

至 Node.js 官網 下載安裝檔並執行，安裝方式和大部份程式一樣，都按下一步即可安裝完成。

## Step 2. 確認 node 及 npm 版本

* 查看 node 版本

        node -v

* 查看 npm 版本

        npm -v

## Step 3. 安裝全域 Vue-cli

        npm install -g vue-cli 

* vue 基本指令表

        vue

* 查看版本（V 須為大寫）

        vue -V

## Step 4. 專案初始化

        vue init <template-name> <project-name>

* 這裡可以使用剛剛有所提到的樣板，也可以使用 vue list 來查看所有的樣板
* 舉個例子

        vue init webpack hello-vue

## Step 5. 環境設定

安裝的同時會需要填寫專案的一些資訊以及環境的設定，依照個人專案的不同而設定

* Project name：專案名稱
* Project description：專案描述
* Author：作者
* Vue build：Runtime + Compiler 及 Runtime-only 兩種
* Install vue-router：是否安裝 vue-router
* Use ESLint to lint your code：是否使用 ESLint 來規範程式碼
* Pick an ESLint preset：Standard、Airbnb 及 none 三種
* Set up unit tests：是否加入單元測試
* Setup e2e tests with Nightwatch：是否加入 e2e 測試
* Should we run `npm install` for you after the project has been created：完成後是否自動執行 npm instal

## Step 6. 安裝專案套件

        cd <project-name>

安裝套件

        npm install

# 執行專案

再來我們要來 run 這個專案了

        npm run dev


* 打開瀏覽器輸入  http://localhost:8080  有畫面出現代表你成功摟

*  那如果想要在 Web Server 上面做使用的話該怎麼辦呢？

        npm run build

這樣的話在專案裡面會出現 dist/ 這個資料夾，這樣你的專案就打包好了

# 安裝 Bootstrap 套件

        npm install bootstrap-vue bootstrap --save

* 打開 main.js 在上面加入

        import BootstrapVue from 'bootstrap-vue/dist/bootstrap-vue.esm';
        上面那行要放在 import App from 'App.vue'; 的上面

        import 'bootstrap/dist/css/bootstrap.css';
        import 'bootstrap-vue/dist/bootstrap-vue.css';

        Vue.use(BootstrapVue);


# 安裝 Jquery 套件

* 打開 package.json 加入

        dependencies:{
               "jquery": "^3.3.1"
        }

使用 npm install

* 打開 webpack.base.conf.js 在裡面加入

        var webpack = require("webpack")

* 找到 module.exports 加入

        plugins: [
                new webpack.optimize.CommonsChunkPlugin('common.js'),
                new webpack.ProvidePlugin({
                        jQuery: "jquery",
                        $: "jquery"
                })
        ]

* 重新 npm run dev

* 在 main.js 引入

        import $ from 'jquery'

# 安裝 Axios 套件
https://www.npmjs.com/package/axios
* 安裝 Axios

        npm install --save axios vue-axios

* Vue Axios 安裝後需加入以下在 main.js 才可以啟用

        import axios from 'axios' 
        import VueAxios from 'vue-axios'

        Vue.use(VueAxios, axios)

* 連接範例資料：https://randomuser.me/


        getData() {
                let vm = this
                this.axios.get('https://randomuser.me/api/?results=50')
                .then(function (response) {
                        // 成功回應
                        console.log(response.data)
                        vm.listData = response.data.results
                })
                .catch(function (error) {
                        // 失敗回應
                        console.log(error);
                });
        }

* Axios 比較

https://segmentfault.com/a/1190000012836882