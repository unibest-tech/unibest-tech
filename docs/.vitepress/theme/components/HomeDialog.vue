<template>
  <ElDialog
    v-model="dialogVisible"
    title="unibest问卷调查（2个问题）"
    :show-close="false"
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

// 控制弹窗显示/隐藏的响应式变量
const dialogVisible = ref(false);

const confirm = () => {
  window.open('https://docs.qq.com/form/page/DVVF0TEdmY2ZHV3RE', '_blank');
  dialogVisible.value = false;
};
</script>
