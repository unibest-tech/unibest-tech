# 快速开始

- 前置依赖

  - **Node.js** - `>=v20` (我的是 `v22.13.0`)
  - **pnpm** - `>=9+` (我的是 `10.11.0`)
  - **`VSCode`** - 可选 `WebStrom`
  - **`HBuilderX`** - `APP` 的运行和发布还是离不开它

> 必看章节：[uni 插件篇](/base/3-plugin) 和 [常见问题](/base/14-faq)

## 创建项目

通过下面的命令可以快速生成项目模板，`pnpm create unibest <项目名称>` ，如果不写 `<项目名称>` 会进入命令行交互模式。

```bash
# 如果没有 pnpm，请先安装: npm i -g pnpm
pnpm create unibest
# 时不时加一下 @latest 标识，这样可以使用最新版本的 create-unibest
pnpm create unibest@latest
```

实际操作截图如下：

`create-unibest` 在 `v1.10.0` 开始会有版本号，如下：

![alt text](./assets/2-2.png)

`2025-06-21` 发布 `v2.0.0` 精简了很多模板，`base`、`tabbar`、`spa` 合并成了新的 `base` 模板（新的 `base` 模板可以在代码层面得到所有的四种 `tabbar` 形式），同时去掉了 `hbx-base`、`hbx-demo`。

最新的模板支持如下：
![alt text](image-1.png)

新的 `base` 模板如何切换不同的 tabbar, 见 [tabbar 专题](./2-tabbar.md)

> 旧的模板相关内容，见文末，留个纪念。

## 安装、运行

```bash [pnpm]
pnpm i
pnpm dev     # 运行h5
pnpm dev:mp  # 运行微信小程序
pnpm dev:app # 运行App
```

`pnpm dev` 之后在浏览器打开 `http://localhost:9000/`。

> 其他平台构建和发布，查看 [运行发布篇](./11-build)。

## 第一次 `commit`

```bash
git add .
git commit -m "feat: init project"
```

## `v3` 代码块

在 `vue` 文件中，输入 `v3` 按 `tab` 即可快速生成页面模板，可以大大加快页面生成。

> 原理：基于 `VSCode` 代码块生成。

![alt text](./assets/2-4.gif)

## 注意事项

- 若代码里面自动引入的 `API` 报错，只需要 `pnpm dev` 即可。
- 若代码运行后，`H5端` 浏览器界面底部没有 `tabbar`， 刷新浏览器或者再次 `pnpm dev` 即可。

## 项目仓库地址

`github` 和 `gitee` 实时同步，代码一致。

### 普通模板：

- https://github.com/unibest-tech/unibest
- https://gitee.com/feige996/unibest

> `demo` 模板是在 `hello-unibest` 项目中，仓库地址如下：

- https://github.com/feige996/hello-unibest
- https://gitee.com/feige996/hello-unibest

> 未来 `github` 上的仓库都可能迁移到 `unibest-tech` 组织下。

## 旧的模板生成相关内容

::: details 下面的在 2025-06-21 发布 v2.0.0 之后过期了

![unibest templates](https://oss.laf.run/ukw0y1-site/xmind/unibest模板.png)

`create unibest` 支持 `-t` 参数选择模板，目前已有两大类 `8` 个模板

- `普通` 模板( `4个` ）：分别是 `base`、`tabbar`、`spa`、 `i18n`、`demo`。
- `hbx` 模板(`2个` ）：分别是 `hbx-base`、`hbx-demo`。

不带 `-t` 参数时会默认生成 `base` 模板。

`base` 模板是最基本的模板，更新最及时，推荐使用 `base` 模板创建新项目。其他几个模板也是基于 `base` 模板得到的。 `demo` 模板则作为参考用。

`base` 模板的改动会自动同步到其他几个分支，通过 `github actions` 实现。

```sh
# VS Code 模板
pnpm create unibest # 默认用 base 模板

pnpm create unibest -t base # 基础模板
pnpm create unibest -t tabbar # 自定义 tabbar 模板
pnpm create unibest -t spa # 单页应用 模板（使用一个组件模拟tabbar）
pnpm create unibest -t i18n # 多语言模板
pnpm create unibest -t demo # 所有demo的模板(包括i18n)
```

> 2024-12-29<周日> 发表了一篇文章：[【unibest】可以去掉 hbx 模版了，base 模板一统天下](https://mp.weixin.qq.com/s/ybunFNkjKfV5yVLOMvqscg?token=1696234630&lang=zh_CN)
>
> 就是说 hbx 模板可以退出历史舞台了。

:::
