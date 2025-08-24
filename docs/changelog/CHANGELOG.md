# CHANGELOG 更新日志

> 完整的更新日志，查看 [github releases 日志](https://github.com/unibest-tech/unibest/releases)

## v3.10.0(2025-08-22)

### 新增 `登录策略`

- 新增 `登录策略` 配置项，用于配置登录时的策略。
  - `DEFAULT_NO_NEED_LOGIN：0`：黑名单策略，默认可以进入 APP
  - `DEFAULT_NEED_LOGIN: 1`：白名单策略，默认不可以进入 APP，需要强制登录
- 外加配套的 `EXCLUDE_PAGE_LIST`: 排除在外的列表，白名单策略指白名单列表，黑名单策略指黑名单列表
- 并编写了配套的 `pages/login/login` 路由和 `pages/me/me` 路由，已经根据登录策略进行了跳转。

## v3.8.0(2025-08-08)

### tabbar 改版

框架内支持 `UI库` 无关的自定义 `tabbar`，以便部分无 `tabbar` 组件的 `UI库` 的接入。

- 支持多种类型的图标( `uniUi Icons, uiLib Icons, unocss Icons, iconfont, image` 等)
- 支持 `tabbar` 中间鼓包 (bulge) 的 `tabbatItem`

### 路由拦截增强

支持直接进入应用路由的的路由拦截，如 `h5` 直接输入路由、`微信小程序` 分享后进入等。

## v3.4.0(2025-07-19)

### 多语言模版

- `tabbar` 和 `navbar` 无需用户自己做多语言的切换操作，框架已经处理好了。

详情请看 [多语言篇-tabbar 标题](/base/10-i18n#tabbar-标题)

## v3.0.0(2025-06-21-周六)

### 重大更新

- 原本的 `base`、`tabbar`、`spa` 合并为新的 `base` 模板。并把新的 `base` 分支重命名为 `main` 分支。详情见 [tabbar 专题](/base/2-tabbar.md)

- 原本的 `main` 分支是文档相关的分支，已经单独放到新的仓库了。

> 掘金文章链接：[🎉 unibest 3.0 发布了！看看都更新了啥好用的功能~](https://juejin.cn/post/7518343357765124136)

### 格式化工具优化

- 鉴于 `oxlint` 暂时还不支持 `vue` 文件，考虑到不少团队很大，无法检测 `vue` 文件确实不妥，就使用了 `antfu` 的 `eslint-config`。

> 注意：等 `oxlint` 支持 `vue` 文件，我们第一时间加回来，真的非常快。

**提交代码的时候会自动触发。** 如果想主动检测，可以使用 `pnpm lint` 命令。

## v2.12.1(2025-06-13)

### `oxlint` 优化

- `oxlint` 从 `0.11.0` 升级到 `1.0.0`。

> 注意：最新的 `1.1.0` 还有问题，运行报错，所以使用 `1.0.0`。（别贪新）

**提交代码的时候会自动触发。** 如果想主动检测，可以使用 `pnpm lint` 命令。

## v2.11.1(2025-06-11)

### `hello-unibest`

- 新增 `echarts`(推荐) 和 `ucharts` 示例。

### docs 文档

- 更新 `App 专题` `热更新`内容。( `android端` 无法热更新的问题，已经解决了！)

## v2.11.0(2025-06-03)

<!-- ### 架构优化

- 把 `v2.8.0(2025-05-20)` 版本删除的 `husky + commitlint` 配置加回来了。 -->

### 依赖降级

- 将 `unocss` 从 `66.0.0` 降级到 `65.4.2`。(因为有部分网友会出现问题，所以降级了。)

### 新模板

- 新增 `base-sard-ui` 模板，方便用户直接使用 `sard-ui` 这个 UI 库开发。

<!-- ## v2.10.1(2025-05-28)

### 新功能

- 实现基础的 `登录` 功能，支持 `微信小程序` 静默登录 和 `非小程序` 登录。 -->

<!-- ## v2.9.3(2025-05-27)

### 新功能

- 支持 `spa` 模板，属于单页应用，完全自定义 `tabbar` 的形式。

### 依赖升级

- 将 `unocss` 从 `0.58` 升级到 `66.0.0`。
- 将 `wot-design-uni` 从 `^1.4.0` 升级到 `^1.9.0`。
- 将 `vue` 从 `3.4.21` 升级到 `^3.5.15`。
- 将 `vite` 从 `5.2.8` 升级到 `6.3.5`。

## v2.8.0(2025-05-20)

### 架构优化

- 移除 `stylelint` 和 `eslint` 配置，统一采用 `oxlint` 进行代码检查，提升代码校验的速度（比 `eslint` 快 `50-100` 倍）。
- ~~移除 `husky` 和 `commitlint` 配置(使用编辑器的AI生成commit信息)。~~(应网友要求，在v2.11.0加回来了)

  ::: details 对于 `v2.8.0` 以下版本，需按以下步骤操作：

  - 把 `stylelint, eslint` 相关依赖包删除
  - 安装 `oxlint`，设置 `lint-staged` 配置为 `oxlint`
  - 删除 `stylelint, eslint` 相关文件

  ![alt text](image-3.png)

  :::

## v2.7.0(2025-05-19)

### 依赖升级

- 将 `@dcloudio/uni-app` 从 `3.0.0-4020920240930001` 升级到 `3.0.0-4060520250512001`，获取最新功能和性能优化。

### 新功能

- 支持 `无 TabBar` 模式，用户只需删除 `pages.config.ts` 中的 `tabBar` 配置即可。

::: details 对于 `v2.7.0` 以下版本，需按以下步骤操作：

- 执行 `pnpm uvm` 升级 `@dcloudio/uni-app`。
- 修改 `src/utils/index.ts` 部分代码：

```ts
import pagesConfig from '@/pages.json'
const { pages, subPackages, tabBar = { list: [] } } = { ...pagesConfig }

/** 判断当前页面是否是 tabbar 页  */
export const getIsTabbar = () => {
  try {
    const lastPage = getLastPage()
    const currPath = lastPage?.route

    return Boolean(tabBar?.list?.some((item) => item.pagePath === currPath))
  } catch {
    return false
  }
}
```

::: -->

## ...

## v0.0.0(2023-12.21)

创建项目，首次提交。
