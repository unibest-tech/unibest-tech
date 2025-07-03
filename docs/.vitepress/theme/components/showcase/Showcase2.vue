<script setup>
import { cases } from './Showcase';
</script>

<template>
  <div class="cases-container">
    <el-card v-for="(item, index) in cases" :key="index" shadow="hover">
      <template #header>
        <span class="case-title">{{ item.name }}</span>
        <span class="case-desc">{{ item.desc }}</span>
      </template>
      <el-image :src="item.image" />
    </el-card>
  </div>
</template>

<style scoped>
.cases-container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 20px;
  margin: 20px 0;
}

.case-title {
  font-size: 18px;
  font-weight: 500;
}

.case-desc {
  margin-left: 10px;
  font-size: 14px;
  color: #999;
}

:deep(.el-card\_\_body .el-image) {
  width: 100%;
  border-radius: 4px;
}
</style>
