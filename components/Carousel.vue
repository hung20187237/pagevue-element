<template>
    <el-carousel :interval="4000" type="card" height="200px">
      <el-carousel-item v-for="tableData in 6" :key="tableData">
        <el-image
            style="width: 100%; height: 100%"
            :src="tableData.url"
            :fit="fit">
        </el-image>
      </el-carousel-item>
    </el-carousel>
  </template>
  
  <style>
    .el-carousel__item h3 {
      color: #475669;
      font-size: 14px;
      opacity: 0.75;
      line-height: 200px;
      margin: 0;
    }
  
    .el-carousel__item:nth-child(2n) {
      background-color: #99a9bf;
    }
  
    .el-carousel__item:nth-child(2n+1) {
      background-color: #d3dce6;
    }
  </style>
  <script>
        export default {
        data() {
            const adata = [];
            const item = {
                url: 'https://fuss10.elemecdn.com/e/5d/4a731a90594a4af544c0c25941171jpeg.jpeg'
            };

            return {
                tableData: item,
                adata
            };
        },
    };
      </script>