<script setup>
import bairun from './佰润.png';
import jinhuopingtai from './进货平台.png';
import chengzhanggui from './橙掌柜.png';
import yundapai from './云打牌.png';
import xinlingshenhui from './心领神绘AI.png';
import jianyimingpian from './简逸名片.png';
import jiansuotong from './监所通.png';
import jiansuoyou from './监所邮.png';
import yinxiaole from './消印乐.png';
import xiangyouxiaozhan from './随享小栈.png';

const cases = [
  {
    name: '佰润',
    desc: '月销200w+',
    image: bairun,
  },
  {
    name: '进货平台',
    desc: '月销200w+',
    image: jinhuopingtai,
  },
  {
    name: '橙掌柜',
    desc: '月销200w+',
    image: chengzhanggui,
  },
  {
    name: '心领神绘AI',
    desc: 'AI绘画、聊天工具，对接midjourney官方API接口生成',
    image: xinlingshenhui,
  },
  {
    name: '随享小栈',
    desc: '帮助你在浮躁社会中沉淀、记录真实生活的社交笔记空间',
    image: xiangyouxiaozhan,
  },
  {
    name: '云打牌记账本',
    desc: '',
    image: yundapai,
  },
  {
    name: '监所通',
    desc: '出入所管理',
    image: jiansuotong,
  },
  {
    name: '监所邮',
    desc: '寄信管理',
    image: jiansuoyou,
  },
  {
    name: '简逸名片',
    desc: '“简逸”数字名片拥有秘书代建功能，为您创建精美名片，用于您的数字社交。',
    image: jianyimingpian,
  },
  {
    name: '消印乐',
    desc: '一个超级简单的去水印小程序',
    image: yinxiaole,
  },
];
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
