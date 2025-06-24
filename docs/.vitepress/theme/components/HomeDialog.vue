<template>
  <div class="flex justify-center mt-10">
    <ElDialog
      v-model="dialogVisible"
      title="unibest问卷调查（2个问题）"
      width="30%"
      class="rounded-lg shadow-lg"
    >
      <p>耽误你20s，完成以下问卷调查，只有2个题目</p>
      <template #footer>
        <div class="flex justify-end gap-2">
          <!-- <ElButton @click="dialogVisible = false">取消</ElButton> -->
          <ElButton type="primary" @click="confirm">确定前往</ElButton>
        </div>
      </template>
    </ElDialog>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

// 控制弹窗显示/隐藏的响应式变量
const dialogVisible = ref(true);

const confirm = () => {
  window.open('https://docs.qq.com/form/page/DVVF0TEdmY2ZHV3RE', '_blank');
  dialogVisible.value = false;
};
</script>
