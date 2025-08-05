# 如何给 npm 包打补丁

背景：使用的 `npm` 包有 `BUG`，在某些环境下有兼容性问题，库作者维护不及时，这个时候就需要给 `npm` 包打补丁。
我们使用的包管理工具是 `pnpm`，下面我来介绍如何使用 `pnpm` 给 `npm` 包打补丁。

- 1. 在 `package.json` 文件中找到你要打补丁的 `npm` 包，然后执行 `pnpm patch <package-name>` 命令。
- 2. 在 node_modules 目录下找到你要打补丁的 `npm` 包，找到您要修改的文件进行修改。
- 3. 执行 `pnpm patch-commit <package-name>` 命令，会生成一个 `patch` 文件。
- 4. 推送到远端，其他用户拉取后执行 `pnpm install` 命令，会自动应用 `patch` 文件。
