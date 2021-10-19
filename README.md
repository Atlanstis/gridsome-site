# gridsome-site

- Gridsome 是一个免费、开源、基于 Vue.js 构建的框架。

> [Gridsome 中文网](https://www.gridsome.cn/)

## 安装

[安装链接](https://www.gridsome.cn/docs/#how-to-install)

针对 gridsome 依赖 sharp，安装过慢的问题，可通过使用淘宝镜像方式解决。

```shell
npm config set sharp_binary_host "https://npm.taobao.org/mirrors/sharp"
npm config set sharp_libvips_binary_host "https://npm.taobao.org/mirrors/sharp-libvips"
```

### 1. Install Gridsome CLI tool

- Using **YARN:**`yarn global add @gridsome/cli`
- Using **NPM:**`npm install --global @gridsome/cli`

### 2. Create a Gridsome project

1. `gridsome create my-gridsome-site` to create a new project
2. `cd my-gridsome-site` to move into project directory
3. `gridsome develop` to start local dev server at `http://localhost:8080`
4. Happy coding 🎉🙌

### 3. Next steps

1. Create `.vue` components in the `src/pages` directory to create page routes.
2. Use `gridsome build` to generate static files in a `/dist` folder

## 开发说明

1. 访问根目录下 static 目录内资源时，可忽略 static 前缀。例：访问 static 目录下，img 目录下 home-bg.png，直接使用 `/img/home-bg.jpg` 路径即可。
