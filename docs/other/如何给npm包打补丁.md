# 如何给 npm 包打补丁

背景：使用的 `npm` 包有 `BUG`，在某些环境下有兼容性问题，库作者维护不及时，这个时候就需要给 `npm` 包打补丁。
我们使用的包管理工具是 `pnpm`，下面我来介绍如何使用 `pnpm` 给 `npm` 包打补丁。

- 1. 在 `package.json` 文件中找到你要打补丁的 `npm` 包，然后执行 `pnpm patch <package-name>` 命令。
- 2. 执行后会有提示，告诉你可以去编辑代码了，还告诉了你如何提交。示例如下

```sh
$ pnpm patch @uni-helper/vite-plugin-uni-layouts
Patch: You can now edit the package at:

  /Users/burtlai/unibest-projects/unibest/node_modules/.pnpm_patches/@uni-helper/vite-plugin-uni-layouts@0.1.11

To commit your changes, run:

  pnpm patch-commit '/Users/burtlai/unibest-projects/unibest/node_modules/.pnpm_patches/@uni-helper/vite-plugin-uni-layouts@0.1.11'

```

- 3. 在 node_modules 目录下找到你要打补丁的 `npm` 包，找到您要修改的文件进行修改。
- 4. 执行第二步的 `pnpm patch-commit` 命令（如 `pnpm patch-commit '/Users/burtlai/unibest-projects/unibest/node_modules/.pnpm_patches/@uni-helper/vite-plugin-uni-layouts@0.1.11'`），会生成一个 `patch` 文件。
- 5. 推送到远端，其他用户拉取后执行 `pnpm install` 命令，会自动应用 `patch` 文件。
