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
import { ref } from 'vue';

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

// 控制弹窗显示/隐藏的响应式变量，初始化为PC端检测结果
const dialogVisible = ref(isPC());

const confirm = () => {
  window.open('https://docs.qq.com/form/page/DVVF0TEdmY2ZHV3RE', '_blank');
  dialogVisible.value = false;
};
</script>
