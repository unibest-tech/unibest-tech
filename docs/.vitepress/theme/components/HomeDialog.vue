<template>
  <ElDialog
    v-model="dialogVisible"
    title="unibest问卷调查（2个问题）"
    :show-close="false"
    :close-on-click-modal="false"
    width="500px"
    style="margin-top: 30vh; max-width: 90%"
    class="rounded-lg shadow-lg"
  >
    <p>耽误你20s，完成以下问卷调查</p>
    <template #footer>
      <div class="flex justify-end gap-2">
        <!-- <ElButton @click="dialogVisible = false">取消</ElButton> -->
        <ElButton type="primary" @click="confirm">确定前往</ElButton>
      </div>
    </template>
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
const STORAGE_KEY = 'userFormSubmitted';

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
  window.open('https://docs.qq.com/form/page/DVVF0TEdmY2ZHV3RE', '_blank');
  dialogVisible.value = false;
  markFormSubmitted();
};
</script>
