# tabbar 专题

tabbar 调查问卷地址：[问卷地址](https://docs.qq.com/form/page/DVVF0TEdmY2ZHV3RE)

## v3.0.0

> 2025-06-21 开始，新的 `base` 模板同时支持旧的 `tabbar` 和 `spa` 模板，这里大致介绍一下使用。(`tabbar` 和 `spa` 模板已经不再需要了。)

`tabbar` 分为 `4 种` 情况：0,1,2,3。

- 0: 'NO_TABBAR' `无 tabbar`
- 1: 'NATIVE_TABBAR' `完全原生 tabbar`
- 2: 'CUSTOM_TABBAR_WITH_CACHE' `有缓存自定义 tabbar`
- 3: 'CUSTOM_TABBAR_WITHOUT_CACHE' `无缓存自定义 tabbar`

---

- 0 `无 tabbar`，只有一个页面入口，底部无 `tabbar` 显示；常用于临时活动页。
- 1 `原生 tabbar`，使用 `switchTab` 切换 tabbar，`tabbar` 页面有缓存。
  - 优势：原生自带的 tabbar，最先渲染，有缓存。
  - 劣势：只能使用 2 组图片来切换选中和非选中状态，修改颜色只能重新换图片（或者用 iconfont）。
- 2 `有缓存自定义 tabbar`，使用 `switchTab` 切换 tabbar，`tabbar` 页面有缓存。使用了第三方 UI 库的 `tabbar` 组件，并隐藏了原生 `tabbar` 的显示。
  - 优势：可以随意配置自己想要的 `svg icon`，切换字体颜色方便。有缓存。可以实现各种花里胡哨的动效等。
  - 劣势：首次点击 tabbar 会闪烁。
- 3 `无缓存自定义 tabbar`，使用 `navigateTo` 切换 `tabbar`，`tabbar` 页面无缓存。使用了第三方 UI 库的 `tabbar` 组件。
  - 优势：可以随意配置自己想要的 svg icon，切换字体颜色方便。可以实现各种花里胡哨的动效等。
  - 劣势：首次点击 `tabbar` 会闪烁，无缓存。

上述文档在代码中也有一份，方便开发者查阅。`src/layouts/fg-tabbar/tabbar.md`

> 注意：`v3.7.0(2025-08-05)` 开始，`tabbar` 相关的代码统一放到 `src/tabbar` 文件夹。

## 如何配置

![alt text](image-4.png)

首先选择使用哪个 `策略`，然后配置对应的 `tabbarList`。关键代码如下：

```ts
// 文件路径为 `src/layouts/fg-tabbar/tabbarList.ts`
// `v3.7.0(2025-08-05)` 开始， `src/tabbar/config.ts`。
/**
 * tabbar 选择的策略，更详细的介绍见 tabbar.md 文件
 * 0: 'NO_TABBAR' `无 tabbar`
 * 1: 'NATIVE_TABBAR'  `完全原生 tabbar`
 * 2: 'CUSTOM_TABBAR_WITH_CACHE' `有缓存自定义 tabbar`
 * 3: 'CUSTOM_TABBAR_WITHOUT_CACHE' `无缓存自定义 tabbar`
 *
 * 温馨提示：本文件的任何代码更改了之后，都需要重新运行，否则 pages.json 不会更新导致错误
 */
export const TABBAR_MAP = {
  NO_TABBAR: 0,
  NATIVE_TABBAR: 1,
  CUSTOM_TABBAR_WITH_CACHE: 2,
  CUSTOM_TABBAR_WITHOUT_CACHE: 3,
};
// TODO：通过这里切换使用tabbar的策略
export const selectedTabbarStrategy = TABBAR_MAP.NATIVE_TABBAR;

// selectedTabbarStrategy==NATIVE_TABBAR(1) 时，需要填 iconPath 和 selectedIconPath
// selectedTabbarStrategy==CUSTOM_TABBAR(2,3) 时，需要填 icon 和 iconType
// selectedTabbarStrategy==NO_TABBAR(0) 时，tabbarList 不生效
export const tabbarList = [
  {
    iconPath: 'static/tabbar/home.png',
    selectedIconPath: 'static/tabbar/homeHL.png',
    pagePath: 'pages/index/index',
    text: '首页',
    icon: 'home',
    iconType: 'uiLib',
  },
  {
    iconPath: 'static/tabbar/example.png',
    selectedIconPath: 'static/tabbar/exampleHL.png',
    pagePath: 'pages/about/about',
    text: '关于',
    icon: 'i-carbon-code',
    // 注意 unocss 的图标需要在 页面上引入一下，或者配置到 unocss.config.ts 的 safelist 中
    iconType: 'unocss',
  },
];
```

`tabbar` 相关配置统一配置在上面这个文件，`pages.config.ts` 已经默认引入。 ^\_^

> 2025-06-21 周六，肝了一整天，留个纪念。

## v3.3.0

> 2025-06-25 v3.3.0 版（重新梳理 tabbar 配置）

上一版本太追求数据的统一管理，但是会让只需要默认配置的用户感到头大。参考 vue 的渐进式开发思路，我们提供从简到繁的配置方案。
默认就是 原生 tabbar，不需要关心 本文件夹里面的内容。(这是默认配置)
需要自定义 tabbar 的才需要关心这个文件。

```ts
/**
 * 2025-06-25 v3.3.0版（重新梳理tabbar配置）
 *
 * 1)原生tabbar，不需要关心 本文件夹里面的内容。(这是默认配置)
 * 2)自定义tabbar（带缓存），保留 `pages.config.ts 的 tabBar配置`，修改本文件对应的代码。
 * 3)自定义tabbar（不带缓存），虽然我认为这是个伪需求，但是问卷调查中确实有人使用这个。要删除 `pages.config.ts 的 tabBar配置`。
 * 4)无tabbar，直接删除 `pages.config.ts 的 tabBar配置`。（同样不需要关心`layouts/fg-tabbar`）
 *
 */

// TODO：是否开启自定义tabbar，默认不开启
// 不开启表示使用原生tabbar，开启表示使用自定义tabbar
export const CUSTOM_TABBAR_ENABLE = false;
// TODO: 是否开启自定义tabbar的无缓存模式，默认不开启
// 开启表示使用自定义tabbar的无缓存模式，并且需要把 `pages.config.ts` 里面的 tabBar 配置删除
export const CUSTOM_TABBAR_NO_CACHE = false;

/**
 * 根据您选择的UI框架，配置相应的字段信息
 * pagePath 需要与 pages.config.ts 里面的 tabBar.list 里面的 pagePath 保持一致，这样才有缓存效果。
 * iconType: uiLib, unocss, local, iconfont。 (`v3.7.0(2025-08-05)` 开始， 增加了 `uniUi`， 可以直接用 uni-cions)
 */
export const tabbarList = [
  {
    pagePath: 'pages/index/index',
    text: '首页',
    icon: 'home',
    // 选用 UI  框架自带的 icon时，iconType 为 uiLib
    iconType: 'uiLib',
  },
  {
    pagePath: 'pages/about/about',
    text: '关于',
    icon: 'i-carbon-code',
    // 注意 unocss 的图标需要在 页面上引入一下，或者配置到 unocss.config.ts 的 safelist 中
    iconType: 'unocss',
  },
];
```

上面的代码已经传到各个主分支了。
