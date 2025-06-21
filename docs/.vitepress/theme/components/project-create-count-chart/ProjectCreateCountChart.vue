<script setup></script>

<template>
  <div class="wrapper">
    <h3 class="title-cls">每天创建 unibest 项目数量图</h3>
    <div class="cases-container">一个图表</div>
  </div>
</template>

<style scoped>
.wrapper {
  position: relative;
  padding: 0 24px;
}
@media (min-width: 640px) {
  .wrapper {
    padding: 0 48px;
  }
}
.title-cls {
  margin: 20px auto;
  max-width: 1152px;
  color: var(--vp-button-brand-bg);
}
.cases-container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 20px;
  margin: 20px auto;
  max-width: 1152px;
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
