<template>
  <el-container style="height: 100vh; border: 1px solid #eee; display: block;" >
    <NavBar/>
    <el-container>
      <el-main>
        <el-container>
          <el-calendar v-model="value"> </el-calendar>
        </el-container>
      </el-main>
    </el-container>
  </el-container>
</template>

<style>
@import url("//unpkg.com/element-ui@2.15.8/lib/theme-chalk/index.css");

.el-header {
  background-color: #b3c0d1;
  color: #333;
  line-height: 60px;
}

.el-aside {
  color: #333;
}
</style>

<script>
import NavBar from "../../components/NavBar.vue";
export default {
  data() {
    return {
      value: new Date(),
    };
  },
  components: { NavBar },
};
</script>
