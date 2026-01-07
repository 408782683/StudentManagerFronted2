<template>
  <div class="app-shell dashboard-shell">
    <div class="page-header">
      <div>
        <h1 class="page-title">教师工作台</h1>
        <p class="page-subtitle">选择要进行的教学任务入口。</p>
      </div>
      <div class="page-meta">
        <el-tag type="warning" effect="dark">教学中心</el-tag>
        <span class="page-meta__text">课程与教学管理</span>
      </div>
    </div>
    <el-row :gutter="20">
      <el-col v-for="card in cards" :key="card.route" :xs="24" :sm="12" :md="8">
        <el-card shadow="hover" class="module-card" @click="go(card.route)">
          <div class="module-card__content">
            <div class="module-card__icon">
              <el-icon :size="24"><component :is="card.icon" /></el-icon>
            </div>
            <div class="module-card__text">
              <div class="module-card__title">{{ card.title }}</div>
              <div class="module-card__desc">{{ card.desc }}</div>
            </div>
          </div>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script setup>
import { useRouter } from 'vue-router';
import { DocumentChecked, Notebook, Collection, Lock } from '@element-plus/icons-vue';

const router = useRouter();
const cards = [
  { title: '教学任务', desc: '查看本学期的授课与带班任务。', route: '/teacher/assignments', icon: Notebook },
  { title: '成绩录入', desc: '录入与查询所授课程成绩。', route: '/teacher/grades', icon: DocumentChecked },
  { title: '课表与点名册', desc: '下载个人课表，导出行政班点名册。', route: '/teacher/timetable', icon: Collection },
  { title: '账号与密码', desc: '修改登录密码，保障账户安全。', route: '/teacher/account', icon: Lock }
];

const go = (route) => router.push(route);
</script>
