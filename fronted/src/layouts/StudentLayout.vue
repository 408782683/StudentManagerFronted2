<template>
  <el-container class="app-layout">
    <el-aside width="240px" class="app-aside">
      <el-menu :default-active="active" router class="app-menu">
        <el-menu-item index="/student/dashboard">工作台</el-menu-item>
        <el-menu-item index="/student/courses">选课</el-menu-item>
        <el-menu-item index="/student/grades">成绩查询</el-menu-item>
        <el-menu-item index="/student/timetable">课表</el-menu-item>
        <el-menu-item index="/student/account">账号安全</el-menu-item>
      </el-menu>
    </el-aside>
    <el-container>
      <el-header class="app-header">
        <div class="app-header__brand">
          <img :src="logo" alt="淮安大学教务系统 logo" class="app-header__logo" />
          <div class="app-header__text">
            <div class="app-header__title">淮安大学教务系统 · 学生中心</div>
          </div>
        </div>
        <div class="app-header__actions">
          <el-tag type="success" effect="dark">{{ user?.role }}</el-tag>
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
import logo from '../logo.png';

const route = useRoute();
const router = useRouter();
const user = computed(() => getUser());
const active = computed(() => route.path);

const logout = () => {
  clearUser();
  router.push('/');
};
</script>
