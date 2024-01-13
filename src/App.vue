<template>
  <div style="display: block; width: 100%; margin: auto;">
    <el-table :data="tableData" height="700" style="width: 100%; border: 1px solid;" class="table">
      <el-table-column prop="date" label="Date" width="180" />
      <el-table-column prop="name" label="Name" width="180" />
      <el-table-column prop="address" label="Address" />
    </el-table>
  </div>
</template>

<script lang="ts" setup>

import axios from "axios";

const tableData = [
  // 你的数据
]

axios.post('/data')
    .then(function (response) {
      // handle success
      console.log(response);
    })
    .catch(function (error) {
      // handle error
      console.log(error);
    })
    .finally(function () {
      // always executed
    });


</script>

<style>
.table {
  border-radius: 10px;
  border: 1px solid; /* 添加边框样式 */
}
</style>