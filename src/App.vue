<template>
  <div style="display: block; width: 100%; margin: auto;">
    <el-table :data="tableData" height="700" style="width: 100%; border: 1px solid;" class="table">
      <el-table-column prop="id" label="id" width="180" />
      <el-table-column prop="date" label="date" width="180" />
      <el-table-column prop="text" label="text" />
    </el-table>
  </div>
</template>

<script lang="ts" setup>

import axios from "axios";
import {reactive, ref} from "vue";

let tableData = [{}]

let a = []
// 向给定ID的用户发起请求
axios.get('http://localhost:8888/ocrData')
    .then(function (response) {
      tableData.pop()
      // 处理成功情
      a = response.data
      for (const val in a) {
        tableData.push({
          "id":a[val][0],
          "text":a[val][2],
          "date":a[val][1]
        })

        console.log(val)
      }
    })
    .catch(function (error) {
      // 处理错误情况
      console.log(error);
    })
    .finally(function () {
    });

</script>

<style>
.table {
  border-radius: 10px;
  border: 1px solid; /* 添加边框样式 */
}
</style>