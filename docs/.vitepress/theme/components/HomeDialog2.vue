<template>
  <ElDialog
    v-model="dialogVisible"
    title="unibest更新了啥？去看看"
    :show-close="false"
    :close-on-click-modal="false"
    width="400px"
    style="margin-top: 30vh; max-width: 90%"
    class="rounded-lg shadow-lg"
  >
    去看看 unibest 发布 3.11 都更新了啥？<br />
    <div
      style="
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 16px;
        text-align: center;
        margin-top: 1em;
      "
    >
      <ElButton type="primary" @click="confirm">去看看</ElButton>
    </div>
  </ElDialog>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

// 判断是否为PC端浏览器
const isPC = () => {
  // 检测userAgent中的移动设备关键词
  const mobileKeywords = [
    'Android',
    'webOS',
    'iPhone',
    'iPad',
    'iPod',
    'BlackBerry',
    'Windows Phone',
  ];
  const isMobile = mobileKeywords.some((keyword) => navigator.userAgent.includes(keyword));

  // 结合屏幕宽度判断，大于768px视为PC端
  return !isMobile && window.innerWidth >= 768;
};

// 本地存储键名常量
const STORAGE_KEY = 'unibest_v3.11.0-dialog-shown';

// 检查本地存储中是否已填写过表单
const checkFormSubmitted = () => {
  try {
    // 尝试读取本地存储，处理可能的浏览器安全限制
    const submitted = localStorage.getItem(STORAGE_KEY);
    return submitted === 'true';
  } catch (e) {
    console.error('读取本地存储失败:', e);
    return false; // 存储不可用时默认视为未填写
  }
};

// 控制弹窗显示/隐藏的响应式变量
const dialogVisible = ref(false);

// 更新弹窗显示状态
const updateDialogVisibility = () => {
  // 仅当PC端且未填写过表单时显示弹窗
  dialogVisible.value = isPC() && !checkFormSubmitted();
};

// 标记表单已填写并保存到本地存储
const markFormSubmitted = () => {
  try {
    localStorage.setItem(STORAGE_KEY, 'true');
    dialogVisible.value = false;
  } catch (e) {
    console.error('保存到本地存储失败:', e);
  }
};

// 窗口大小变化时重新检测
const handleResize = () => {
  updateDialogVisibility();
};
onMounted(() => {
  // 初始检查
  updateDialogVisibility();
  // 添加窗口大小变化监听
  window.addEventListener('resize', handleResize);
});

onUnmounted(() => {
  window.removeEventListener('resize', handleResize);
});

const confirm = () => {
  window.open('/blog/2', '_blank');
  dialogVisible.value = false;
  markFormSubmitted();
};
</script>
