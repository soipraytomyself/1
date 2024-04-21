1. ###### 安装`Node.js`和`npm`。

    首先，新版的`Node.js`中包含`npm`，只需要安装`Node.js`即可。
    具体的安装教程可以百度(考虑到大部分同学的开发环境是Windows，而Windows的安装比较简单，下载安装包按照提示安装即可)。
    安装完成后，检查一下是否安装成功。打开命令行(`cmd`)，输入

    - 检查`Node.js`版本
      ```powershell
      node -v
      ```
    - 检查`npm`版本
      ```powershell
      npm -v
      ```

    如果无法显示版本号，可能是环境变量配置等问题(很常见了)，同样的，因为不是今天分享的重点，所以如果出现这样的问题可以百度解决。

    

2. ###### 关于`npm`换源

    - 一种方法是每次使用`npm install`命令时，在后面加参数使用淘宝源，即
      ```powershell
      npm install <packageName> --registry=https://registry.npm.taobao.org
      ```
    - 另一种方法是安装`cpnm`
      ```powershell
      npm install -g cnpm --registry=https://registry.npm.taobao.org
      ```
      之后使用`cpnm`命令(本质也是淘宝还原)，即
      
      ```
      cnpm install <packageName>
      ```

    方便起见，后面的命令都用`npm`，但你可以自行选择是否换源、用哪种换源方式。

    

3. ###### `Vue`和`Vue CLI`的区别

    - `Vue`全称是`Vue.js`，是一套用于构建用户界面的渐进式`JavaScript`框架。
    - `Vue CLI`是一个脚手架，通俗地说，`Vue CLI = Vue + JS plugins`。`Vue CLI`是代码生成器，可以快速生成一套基于`Vue`完整的前端框架，单独编译，单独部署；可以再集成各种第三方插件，扩展出更多的功能。
    - 对应关系
      | `Vue CLI`版本 | `Vue`版本       |
      | ------------- | --------------- |
      | `< 4.5`       | `Vue 2`         |
      | `>= 4.5`      | `Vue 2`/`Vue 3` |

    

4. ###### 安装`Vue CLI`

    至于为什么不安装`Vue`后面解释
    用`npm`或`cnpm`安装某个版本的`Vue CLI`。

    ```powershell
    npm install -g @vue/cli@3.11.0
    ```
    检查是否安装成功
     ```powershell
    vue -V
     ```

    

5. ###### 新建项目

    ```powershell
    vue init webpack <projectName>
    ```
    ![自选项](https://upload-images.jianshu.io/upload_images/17668206-0ac90e23d63b537d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/650)
    | 选项                |                              |
    | ------------------- | ---------------------------- |
    | Project name        | 项目名称，回车默认           |
    | Project description | 项目描述，回车默认           |
    | Author              | 作者，回车默认               |
    | Vue build           | 选择推荐项                   |
    | Install vue-router  | 路由插件，建议是             |
    | Use ESLint          | 代码风格管理插件，新手建议否 |

    

6. ###### 安装依赖

    如果上一步没有选择自动安装依赖，需要自行运行

    ```powershell
    npm install
    ```

    

7. ###### 工具推荐

    - 编辑器：`VS Code`。轻量化，适合写前端页面。
    - 扩展：`Vetur`。`Vue`代码高亮(包括`HTML`、`CSS`、`JS`)，npm脚本可视化等。

    

8. ###### 目录结构

    Vue项目的目录结构如图所示
    ![目录结构](https://upload-images.jianshu.io/upload_images/17668206-daea67d1e5b79f8b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

    | 目录   | 说明                                                         |
    | ------ | ------------------------------------------------------------ |
    | bulid  | 操作文件，运行`npm run *`时执行的就是这里的文件              |
    | config | 配置文件，执行文件的配置信息                                 |
    | src    | 基本所有的源代码以及图片都放在这个文件夹下，也是我们主要编写部分主要涉及的文件夹 |

    `src`子目录如下
    ![image.png](https://upload-images.jianshu.io/upload_images/17668206-85d90b3c84412652.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

    | 子目录     | 说明                           |
    | ---------- | ------------------------------ |
    | assets     | 资源文件夹，放图片等资源       |
    | components | 组件文件夹，放自定义组件       |
    | router     | 路由文件夹，决定页面的跳转规则 |
    | App.vue    | 应用组件，挂载所有自己写的组件 |
    | main.js    | webpack入口文件                |

    

9. ###### 运行项目

     ```powershell
     cd demo
     npm run dev
     ```
     ![主页](https://upload-images.jianshu.io/upload_images/17668206-05c776eaf9c25dea.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/650)

     

10. ###### 学会路由跳转

     在`src/router`目录下的`index.js`文件中添加

     ```javascript
     {
       path: '/tutorial',
       name: '从零开始搭建Vue项目',
       component: () => import('@/views/tutorial/index'),
     },
     ```
     同时，在`src`目录下新建`views`文件夹，下面新建`tutorial`文件夹，下面新建`index.vue`文件。
     ![image.png](https://upload-images.jianshu.io/upload_images/17668206-2be44a5a9106b472.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
     其中写入

     ```vue
     <template>
     <div>
       <h1>从零构建Vue项目</h1>
     </div>
     </template>
     
     <script>
     export default {};
     </script>
     
     <style>
     </style>
     ```
     这样，我们就新建了一个页面，这个页面的内容是“从零构建Vue项目”，这个页面的路由是`/tutorial`，这个页面对应的文件在`src/views/tutorial/index.vue`。但是用户如何访问到这个页面呢？比较原始的方法就是改地址。但是我们有更用户友好的方法，在`HelloWord.vue`(我们发现主页页面在这里)中添加一个路由链接

     ```html
     <router-link to="/tutorial">从零开始搭建Vue项目</router-link>
     ```
     其中，`to`参数后面是跳转目标的路由，加`/`表示从根路由开始，不加`/`表示从当前路由开始(后面会演示)。刷新主页，变成了
     ![主页.png](https://upload-images.jianshu.io/upload_images/17668206-7c6f32297c6e1361.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/650)
     点击最下面那行字，我们跳转到
     ![新建页.png](https://upload-images.jianshu.io/upload_images/17668206-4d0903d458467774.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/650)
     可以看到成功了！

     （屏蔽Vue图标的方法：注释掉`App.vue`中的`<img src="./assets/logo.png">`）

     

11. ###### `Vue`文件结构

      | 模块                                             | 功能       | 语言         |
      | ------------------------------------------------ | ---------- | ------------ |
      | template                                         | 内容       | `html`       |
      | script                                           | 数据与方法 | `javascript` |
      | style                                            | 样式       | `css`        |
      | 接下来对页面进行一些扩充，来理解三个部分的作用。 |            |              |
      | 添加一个按钮                                     |            |              |
      ```html
      <button>新增</button>
      ```
      前端页面的“内容”就放在`template`中，相当于我们告诉`Vue`框架，这个页面有两个内容，先是一个标题，标题叫“从零构建Vue项目”；然后是一个按钮，按钮文字是“新增”。
      但是，如果我们想让这个按钮变成蓝色呢？在按钮上添加类，然后再`style`模块编写类的具体内容。

      ```html
      <button class="my-button">新增</button>
      ```
      ```css
      .my-button {
        background-color: yellow;
      }
      ```
      看看效果
      ![修改前](https://upload-images.jianshu.io/upload_images/17668206-c3ee51e76abb00c2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/650)
      ![修改后](https://upload-images.jianshu.io/upload_images/17668206-7985e60141f1b687.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/650)
      所以，我们在`template`中定义内容有什么，在`style`模块定义内容长什么样，也就是“样式”。
      那么`script`的作用是什么呢？前面讲到数据和方法，那么先说数据。`Vue.js`使用了基于`HTML`的模板语法，允许开发者声明式地将`DOM`绑定至底层组件实例的数据。所有`Vue.js`的模板都是合法的`HTML`，所以能被遵循规范的浏览器和`HTML`解析器解析(官方文档)。
      ```html
      <button class="my-button">{{ buttonText }}</button>
      ```
      ```javascript
      data() {
        return {
          buttonText: "功德",
        };
      },
      ```
      这意味着我们可以动态的绑定“内容”中的数据，如果在操作中修改了变量，那么页面展示的内容也会改变
      ```html
      <button class="my-button" @click="handleClick">{{ buttonText }}</button>
      <input :value="count"/>
      ```
      ```javascript
      methods: {
        handleClick() {
          this.count += 1;
        },
      },
      ```
      我们在旁边再添加一个数据`count`。这里涉及到vue的一个缩写，`@click`等价于`v-on:click`，意为监听点击事件的函数。然后在`scipt`里的`methods`中编写对应函数——这就是所谓“数据与操作”中的“操作”。看下效果
      ![每次点击+1](https://upload-images.jianshu.io/upload_images/17668206-b0cafb54be4d4671.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/650)

      换成`v-model`。区分`:value`和`v-model`。

      ```
      <input v-model="count"/>
      
      this.count = Number(this.count) + 1;
      ```

      到目前为止，我们已经基本理解了`Vue`文件的结构。

      

12. ###### 前后端连接

      实际上，目前为止还停留在前端界面的开发。实际开发中一定是需要和后端的数据库进行交互的。
      什么叫“前后端分离”？什么叫“前后端不分离”(django)？简而言之，就是前端只需要知道和后端交互的接口，而不管后端开发的逻辑，双方通过约定好的数据格式交互(一般为`json`文件)。这样的好处是利于团队开发。
      `Vue`常用的交互插件为`axios`。安装

      ```powershell
      npm install axios
      ```
      使用
      ```javascript
      import axios from "axios";
      
      export default {
        created() {
          axios({
            method: "get",
            url: "http://jsonplaceholder.typicode.com/posts",
          }).then((response) => {
            console.log(response);
          });
        },
      };
      ```
      控制台数据
      ![后端返回](https://upload-images.jianshu.io/upload_images/17668206-d0587fcc22a3856a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
      发现：任何语言，哪怕换了框架都可以！

      ```
      axios({
        method: "get",
        url: "http://jsonplaceholder.typicode.com/posts",
      }).then((response) => {
        console.log(response)
        this.data = response.data
      });
      console.log(this.data)
      ```

      同步/异步问题

      

13. ###### Element-UI的使用

      `el-button`的使用

      `el-table`的使用

      

14. ###### 结语

      ![恭喜你](https://upload-images.jianshu.io/upload_images/17668206-8b99eabc3954e264.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
      实际上，了解了基本原理，任何复杂的架构都是再次基础上建立的。
      需要学习的内容

      | 内容                | 推荐教程 | 说明                     |
      | ------------------- | -------- | ------------------------ |
      | `html`&`css`        |          | 样式方面                 |
      | `element-ui`        | 官方文档 | 更简单的构建组件，搭积木 |
      | `vue`               | 官方文档 | 系统学习                 |
      | `vue-element-admin` | 官方文档 | 后台管理系统模板(常用)   |
      | trick               |          |                          |
      - 控制台调试：请求、元素与样式、日志
      - `Rester`/`postman`: 请求