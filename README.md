# 🧱 Vue2-Common · Vue 2 通用项目模板

[![Vue](https://img.shields.io/badge/Vue-2.6-4FC08D?style=flat-square&logo=vue.js)](https://v2.vuejs.org/)
[![Vue CLI](https://img.shields.io/badge/Vue%20CLI-5.x-3EB489?style=flat-square)](https://cli.vuejs.org/)
[![Element UI](https://img.shields.io/badge/Element%20UI-2.15-409EFF?style=flat-square)](https://element.eleme.io/)
[![Vuex](https://img.shields.io/badge/Vuex-3.x-FFD859?style=flat-square)](https://vuex.vuejs.org/)

一套可直接开工的 Vue 2 工程骨架：路由、状态、请求、自定义指令、rem 适配全部配好，开箱即用。

## 快速开始

```bash
# 安装依赖
npm i

# 启动开发服务器（自动打开浏览器）
npm run dev

# 打包生产版本
npm run build

# 代码审查
npm run lint
```

## 技术栈

| 分类 | 选型 |
| --- | --- |
| 框架 | Vue 2.6 |
| 构建 | Vue CLI 5（`@vue/cli-service`） |
| UI | Element UI 2.15（已全局注册） |
| 状态 | Vuex 3 |
| 路由 | Vue Router 3 |
| 请求 | axios 二次封装 |
| 样式 | Sass + `postcss-px2rem` |
| 代码规范 | ESLint + Prettier |

## 已配置能力

### 全局路径别名

`@` 指向 `src`，无需相对路径层层回退。

### 全局样式与重置

`src/assets/css/reset.scss` 统一浏览器默认样式；`src/assets/sass/main.scss` 承载主题变量。

### axios 请求封装

`src/utils/request.js` 已封装实例创建、请求/响应拦截、loading 与消息提示、401 跳转登录。接口按业务分文件放到 `src/api`：

```javascript
// src/api/test.js
import request from '@/utils/request';

// get 请求
export const getList = () => {
  return request({ url: '/XXX/list', method: 'get' });
};

// post 请求
export const postSave = (data) => {
  return request({ url: '/XXX/save', method: 'post', data });
};
```

`baseURL` 从环境变量 `VUE_APP_BASE_API` 读取，按 `.env.development` / `.env.production` 区分环境。

### 自定义指令

`src/utils/directives.js` 提供常用指令，包括对话框拖拽、全屏、图片懒加载。

### PC 端 rem 适配

`src/utils/rem.js` 以 1920 设计稿为基准等比缩放，根节点 `fontSize` 上限放大 2 倍。浏览器缩放与系统缩放设置下布局保持稳定。若要改为 750 设计稿，修改文件顶部的基准宽度即可。

## 目录结构

```text
Vue2-Common/
├─ src/
│  ├─ api/              接口定义（按业务分文件）
│  ├─ assets/
│  │  ├─ css/reset.scss 样式重置
│  │  └─ sass/          主题与主样式
│  ├─ components/       通用组件
│  ├─ router/           路由表
│  ├─ store/            Vuex 状态
│  ├─ utils/
│  │  ├─ request.js     axios 封装
│  │  ├─ directives.js  自定义指令
│  │  └─ rem.js         rem 适配
│  ├─ views/            页面
│  ├─ App.vue
│  └─ main.js
├─ package.json
└─ README.md
```

## 常见问题

**接口 404？**
检查 `.env.development` 里的 `VUE_APP_BASE_API` 是否指向正确的后端地址，以及是否配置了代理。

**rem 适配后字体偏大或偏小？**
调整 `src/utils/rem.js` 里的 `baseSize`（基准字号）与 `1920`（设计稿宽度），使其与实际设计稿一致。

**Element UI 组件样式不生效？**
确认 `src/main.js` 中已 `Vue.use(ElementUI)` 且引入了 `element-ui/lib/theme-chalk/index.css`。

## 许可

仅供学习与参考使用。
