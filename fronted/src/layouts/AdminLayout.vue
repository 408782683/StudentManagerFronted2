<template>
  <el-container class="app-layout">
    <el-aside width="240px" class="app-aside">
      <el-menu :default-active="active" router class="app-menu">
        <el-menu-item index="/admin/base">工作台</el-menu-item>
        <el-menu-item index="/admin/students">学生管理</el-menu-item>
        <el-menu-item index="/admin/teachers">教师管理</el-menu-item>
        <el-menu-item index="/admin/org">学院/专业/班级</el-menu-item>
        <el-menu-item index="/admin/course-plan">课程与培养计划</el-menu-item>
        <el-menu-item index="/admin/assignments">教学任务分配</el-menu-item>
        <el-menu-item index="/admin/timetable">课表管理</el-menu-item>
      </el-menu>
    </el-aside>
    <el-container>
      <el-header class="app-header">
        <div class="app-header__brand">
          <el-icon class="app-header__icon"><i-ep-suitcase /></el-icon>
          <div class="app-header__text">
            <div class="app-header__title">淮安大学教务系统 · 管理员中心</div>
            <div class="app-header__subtitle">Huai'an University Academic Admin Portal</div>
          </div>
        </div>
        <div class="app-header__actions">
          <el-tag type="danger" effect="dark">{{ user?.role }}</el-tag>
          <span class="app-header__user">{{ user?.name || user?.username }}</span>
          <el-button size="small" type="text" class="app-header__logout" @click="logout">退出</el-button>
        </div>
      </el-header>
      <el-main class="app-main">
        <router-view />
      </el-main>
    </el-container>
  </el-container>
</template>

<script setup>
import { computed } from 'vue';
import { useRoute, useRouter } from 'vue-router';
import { getUser, clearUser } from '../utils/auth';
import { Suitcase as IepSuitcase } from '@element-plus/icons-vue';

const route = useRoute();
const router = useRouter();
const user = computed(() => getUser());
const active = computed(() => route.path);

const logout = () => {
  clearUser();
  router.push('/');
};
</script>
