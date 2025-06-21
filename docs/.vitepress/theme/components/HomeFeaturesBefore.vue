<script setup lang="ts">
// 直接使用Vite注入的构建时变量
import { ref, onMounted } from 'vue';

const version = ref<string>('2.13.1'); // 默认版本号
const repoOwner = 'unibest-tech';
const repoName = 'unibest';
const branch = 'main'; // 假设使用main分支

onMounted(async () => {
  try {
    // 通过GitHub API获取远程package.json
    const response = await fetch(
      `https://raw.githubusercontent.com/${repoOwner}/${repoName}/${branch}/package.json`
    );

    if (response.ok) {
      const packageJson = await response.json();
      version.value = packageJson.version || version.value;
    }
  } catch (error) {
    console.error('Failed to fetch version:', error);
    // 出错时保持默认版本
  }
});
</script>

<template>
  <div>我是优秀案例</div>
</template>
