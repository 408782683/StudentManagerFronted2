<template>
  <div class="app-shell dashboard-shell">
    <div class="page-header">
      <div>
        <h1 class="page-title">管理员工作台</h1>
        <p class="page-subtitle">请选择要进入的业务模块，完成对应的教务管理任务。</p>
      </div>
      <div class="page-meta">
        <el-tag type="danger" effect="dark">管理中心</el-tag>
        <span class="page-meta__text">教务核心管理入口</span>
      </div>
    </div>
    <el-row :gutter="20">
      <el-col v-for="card in cards" :key="card.route" :xs="24" :sm="12" :md="8" :lg="6">
        <el-card shadow="hover" class="module-card" @click="go(card.route)">
          <div class="module-card__content">
            <div class="module-card__icon">
              <el-icon :size="26"><component :is="card.icon" /></el-icon>
            </div>
            <div class="module-card__text">
              <div class="module-card__title">{{ card.title }}</div>
              <div class="module-card__desc">{{ card.desc }}</div>
              <el-tag size="small" type="info" effect="light">{{ card.badge }}</el-tag>
            </div>
          </div>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script setup>
import { useRouter } from 'vue-router';
import { School, Collection, Notebook, SetUp, List, Upload } from '@element-plus/icons-vue';

const router = useRouter();
const cards = [
  { title: '学生管理', desc: '录入、查询、更新和删除学生信息。', route: '/admin/students', badge: '学生', icon: School },
  { title: '教师管理', desc: '维护教师档案、联系方式与任教信息。', route: '/admin/teachers', badge: '教师', icon: Collection },
  { title: '学院 / 专业 / 班级', desc: '维护院系层级、专业与班级关联。', route: '/admin/org', badge: '组织', icon: Notebook },
  { title: '课程与培养计划', desc: '配置课程与学期培养计划。', route: '/admin/course-plan', badge: '课程', icon: SetUp },
  { title: '教学任务分配', desc: '为计划分配授课教师并查看历史记录。', route: '/admin/assignments', badge: '任务', icon: List },
  { title: '课表管理', desc: '上传并管理专业 / 教师 / 学生课表文件。', route: '/admin/timetable', badge: '课表', icon: Upload }
];

const go = (route) => router.push(route);
</script>
