---
title: Vue3+Ant Design 
date: 2022-11-18T21:25:23Z
lastmod: 2022-11-18T21:33:28Z
---

# Vue3+Ant Design 

# 配置方法

1. 安装 `npm install ant-design-vue --save`​
2. 配置 vite 实现按需引入 

    1. 安装依赖`​ npm i unplugin-vue-components -D`​

        修改`vite`​配置文件
    2. ```js
        import Components from "unplugin-vue-components/vite";
        import { AntDesignVueResolver } from "unplugin-vue-components/resolvers";
        import { fileURLToPath, URL } from "node:url";

        import { defineConfig } from "vite";
        import vue from "@vitejs/plugin-vue";

        // https://vitejs.dev/config/
        export default defineConfig({
            plugins: [
                vue(),
                Components({
                    resolvers: [AntDesignVueResolver()],
                }),
            ],
            resolve: {
                alias: {
                    "@": fileURLToPath(new URL("./src", import.meta.url)),
                },
            },
        });

        ```

‍
