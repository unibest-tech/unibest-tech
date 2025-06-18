<script setup lang="ts">
import { ref, onMounted } from 'vue';

const version = ref('2.13.0'); // 默认版本号
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
  <span
    style="
      display: inline-block;
      padding: 0px 8px;
      margin-left: 4px;
      font-size: 10px;
      font-weight: 700;
      color: var(--vp-button-brand-text);
      background-color: var(--vp-button-brand-bg);
      border-radius: 16px;
    "
  >
    {{ version }}
  </span>
</template>
