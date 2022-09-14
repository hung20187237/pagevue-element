<template>
  <el-container style="display: flex">
    <el-aside width="80%" style="background-color: rgb(238, 241, 246)">
      <el-menu 
        :default-active="activeIndex2"
        class="el-menu-demo"
        mode="horizontal"
        @select="handleSelect"
        background-color="#545c64"
        text-color="#fff"
        active-text-color="#ffd04b"
        style="display: flex;justify-content: space-between;" 
      >
        <el-menu-item index="1"><NuxtLink to="/timeline" style="text-decoration: none">TimePicker</NuxtLink></el-menu-item>
        <el-submenu index="2">
          <template slot="title">Workspace</template>
          <NuxtLink to="/workspace" style="text-decoration: none"><el-menu-item index="2-1">Character</el-menu-item></NuxtLink>
          <NuxtLink to="/workspace/planet" style="text-decoration: none"><el-menu-item index="2-2">Planet</el-menu-item></NuxtLink>
          <NuxtLink to="/workspace/starship" style="text-decoration: none"><el-menu-item index="2-3">StarShip</el-menu-item></NuxtLink>
          <NuxtLink to="/workspace/starship" style="text-decoration: none"><el-menu-item index="2-4">StarShip</el-menu-item></NuxtLink>
        </el-submenu>
        <el-menu-item index="3">
          <NuxtLink to="/processcenter" style="text-decoration: none">Processing Center</NuxtLink>
        </el-menu-item>
        <el-menu-item index="4">
          <NuxtLink to="/" style="text-decoration: none">Home</NuxtLink>
        </el-menu-item
        >
      </el-menu>
    </el-aside>
    <el-container>
      <el-header style="font-size: 12px; text-align: right;">
        <el-dropdown>
          <i class="el-icon-setting" style="margin-right: 15px"></i>
          <el-dropdown-menu slot="dropdown">
            <el-dropdown-item>Logout</el-dropdown-item>
            <el-dropdown-item>Add</el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>
        <el-avatar
          style="vertical-align: middle"
          src="https://cube.elemecdn.com/0/88/03b0d39583f48206768a7534e55bcpng.png"
        ></el-avatar>
        <span>Tom</span>
      </el-header>
    </el-container>
  </el-container>
</template>


<script>
export default {
  data() {
    return {
      activeIndex: "1",
      activeIndex2: "2",
    };
  },
  methods: {
    handleSelect(key, keyPath) {
      console.log(key, keyPath);
    },
  },
};
</script>
