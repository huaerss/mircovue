## 搭建微前端项目

### 1.创建对应文件夹 

初始化需要用到的项目 例如vue2 vue3 react 等

### 2.使用monorepo模式

在根目录新建一个 pnpm-workspace.yaml 配置依赖项

```yaml
packages:
  # all packages in direct subdirs of packages/
  - 'vue2'
  # all packages in subdirs of components/
  - 'vue3'
```

配置完成后install一次就行

### 3.使用

```
vue2 pnpm i wujie-vue2 -S
vue3 pnpm i wujie-vue3 -S
react pnpm i wujie-react -S
```

主应用的main.ts

```javascript
import { createApp } from 'vue'
import App from './App.vue'
import Wujie from 'wujie-vue3'
createApp(App).use(Wujie).mount('#app')
```

主应用hellowWord url填写子应用的url 子应用通过npm run dev启动获取对应的url name参数为唯一

```html
 <div>
    <WujieVue width="100%" height="100%" name="唯一值" :url="子应用的url " ></WujieVue>
  </div>
```

### 4.打包

在主项目中pnpm build打包