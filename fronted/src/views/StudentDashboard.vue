<template>
  <div class="app-shell dashboard-shell">
    <div class="page-header">
      <div>
        <h1 class="page-title">学生工作台</h1>
        <p class="page-subtitle">请选择你要进行的学习与查询入口。</p>
      </div>
      <div class="page-meta">
        <el-tag type="success" effect="dark">Student Space</el-tag>
        <span class="page-meta__text">学习与查询服务</span>
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
import { Notebook, DataAnalysis, Collection, Lock } from '@element-plus/icons-vue';

const router = useRouter();
const cards = [
  { title: '选课中心', desc: '查看可选课程并提交选课申请。', route: '/student/courses', icon: Notebook },
  { title: '成绩查询', desc: '查看并打印个人成绩单。', route: '/student/grades', icon: DataAnalysis },
  { title: '课表下载', desc: '按学期获取个人课表文件。', route: '/student/timetable', icon: Collection },
  { title: '账号与密码', desc: '修改登录密码，保障账户安全。', route: '/student/account', icon: Lock }
];

const go = (route) => router.push(route);
</script>
