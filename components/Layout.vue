<template>
  <el-container style="height: 100vh; border: 1px solid #eee">
    <el-aside width="200px" style="background-color: rgb(238, 241, 246)">
      <el-menu :default-openeds="['1']">
        <el-submenu index="1">
          <template slot="title"
            ><i class="el-icon-message"></i>Navigator One</template
          >
          <el-menu-item-group>
            <template slot="title">Group 1</template>
            <el-menu-item
              index="1-1"
              v-on:click="
                adata = tableData;
                index = '1';
              "
              >Option 1</el-menu-item
            >
            <el-menu-item
              index="1-2"
              v-on:click="
                adata = tableData2;
                index = '1';
              "
              >Option 2</el-menu-item
            >
          </el-menu-item-group>
          <el-menu-item-group title="Group 2">
            <el-menu-item
              index="1-3"
              v-on:click="
                adata = tableData3;
                index = '1';
              "
              >Option 3</el-menu-item
            >
          </el-menu-item-group>
          <el-submenu index="1-4">
            <template slot="title">Option4</template>
            <el-menu-item
              index="1-4-1"
              v-on:click="
                adata = tableData4;
                index = '1';
              "
              >Option 4-1</el-menu-item
            >
          </el-submenu>
        </el-submenu>
        <el-submenu index="2">
          <template slot="title"
            ><i class="el-icon-menu"></i>Navigator Two</template
          >
          <el-menu-item-group>
            <template slot="title">Group 1</template>
            <el-menu-item v-on:click="index = '2-1'">Option 1</el-menu-item>
            <el-menu-item v-on:click="index = '2-2'">Option 2</el-menu-item>
          </el-menu-item-group>
          <el-menu-item-group title="Group 2">
            <el-menu-item index="2-3" v-on:click="index = '2-3'">Option 3</el-menu-item>
          </el-menu-item-group>
          <el-submenu index="2-4">
            <template slot="title">Option 4</template>
            <el-menu-item index="2-4-1">
              <NuxtLink to="/timeline" style="text-decoration: none">Option 4-1</NuxtLink>
            </el-menu-item>
          </el-submenu>
        </el-submenu>
        <el-submenu index="3">
          <template slot="title"
            ><i class="el-icon-setting"></i>Navigator Three</template
          >
          <el-menu-item-group>
            <template slot="title">Group 1</template>
            <el-menu-item index="3-1">Option 1</el-menu-item>
            <el-menu-item index="3-2">Option 2</el-menu-item>
          </el-menu-item-group>
          <el-menu-item-group title="Group 2">
            <el-menu-item index="3-3">Option 3</el-menu-item>
            <el-menu-item index="3-3-1">Option any</el-menu-item>
          </el-menu-item-group>
          <el-submenu index="3-4">
            <template slot="title">Option 4</template>
            <el-menu-item index="3-4-1">Option 4-1</el-menu-item>
          </el-submenu>
        </el-submenu>
      </el-menu>
    </el-aside>

    <el-container>
      <el-header style="font-size: 12px; text-align: right;">
        <el-dropdown >
          <i class="el-icon-setting" style="margin-right: 15px"></i>
          <el-dropdown-menu slot="dropdown">
            <el-dropdown-item>Logout</el-dropdown-item>
            <el-dropdown-item>Add</el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>
        <el-avatar style="vertical-align: middle;"
          src="https://cube.elemecdn.com/0/88/03b0d39583f48206768a7534e55bcpng.png"
        ></el-avatar>
        <span>Tom</span>

      </el-header>

      <el-main>
        <Carousel v-if="index === '2-1'" />
        <ListCard v-else-if="index === '2-2'" />
        <Form1 v-else-if="index === '2-3'"/>
        <el-table :data="adata" v-else>
          <el-table-column prop="date" label="Date" width="140">
          </el-table-column>
          <el-table-column prop="name" label="Name" width="120">
          </el-table-column>
          <el-table-column prop="address" label="Address"> </el-table-column>
        </el-table>
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
import Carousel from "./Carousel.vue";
import ListCard from "./ListCard.vue";
import Form from "./Form.vue";
import Form1 from "./Form.vue";
export default {
  data() {
    var index;
    const adata = [];
    const item = {
      date: "2016-05-02",
      name: "Tom",
      address: "No. 189, Grove St, Los Angeles",
    };
    const item2 = {
      date: "2022-08-02",
      name: "Jessy",
      address: "No. 189, Grove St, Los Angeles",
    };
    const item3 = {
      date: "2022-09-10",
      name: "Cobby",
      address: "No. 189, Grove St, Los Angeles",
    };
    const item4 = {
      date: "2022-3-22",
      name: "Inhil",
      address: "No. 189, Grove St, Los Angeles",
    };
    return {
      tableData: Array(20).fill(item),
      tableData2: Array(20).fill(item2),
      tableData3: Array(20).fill(item3),
      tableData4: Array(20).fill(item4),
      isShow: true,
      index,
      adata,
    };
  },
  components: { Carousel, ListCard, Form, Form1 },
};
</script>
