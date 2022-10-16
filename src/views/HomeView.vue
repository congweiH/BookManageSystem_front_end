<template>
  <div>
    <!-- 搜索 -->
    <header style="margin-bottom: 20px;">
      <el-input v-model="params.name" placeholder="请输入名称" style="width: 240px;"></el-input>
      <el-input v-model="params.phone" placeholder="请输入联系方式" style="width: 240px; margin-left: 5px;"></el-input>
      <el-button @click="load" type="primary" style="margin-left: 5px;"><i class="el-icon-search"></i> 搜索</el-button>
      <el-button @click="reset" type="warning" style="margin-left: 5px;"><i class="el-icon-refresh"></i> 重置</el-button>
    </header>

    <!-- 表格 -->
    <el-table :data="tableData" stripe>
      <el-table-column prop="name" label="名称"></el-table-column>
      <el-table-column prop="age" label="年龄"></el-table-column>
      <el-table-column prop="address" label="地址"></el-table-column>
      <el-table-column prop="phone" label="电话"></el-table-column>
      <el-table-column prop="sex" label="性别"></el-table-column>
    </el-table>

    <!-- 分页 -->
    <el-pagination
      style="margin-top: 20px;"
      background
      layout="prev, pager, next"
      :current-page="params.pageNum"
      :page-size="params.pageSize"
      :total="total"
      @current-change="currentChange">
    </el-pagination>
  </div>
</template>

<script>
import request from '@/utils/request.js';

export default {
  name: 'HomeView',
  data() {
    return {
      tableData: [],
      total: 0, 
      params: {
        pageNum: 1,
        pageSize: 10,
        name: '',
        phone: '',
      }
    }
  },
  created() {
    this.load();
  },
  methods: {
    load() {
      // fetch('http://localhost:18103/user/list').then(res => res.json()).then(res => {
      //   this.tableData = res;
      // });
      request.get('/user/page', {
        params: this.params
      }).then(res => {
        if(res.code === '200') {
          this.tableData = res.data.list;
          this.total = res.data.total;
        }
      })
    },
    reset() {
      this.params = {
        pageNum: 1,
        pageSize: 10,
        name: '',
        phone: '',
      };
      this.load();
    },
    currentChange(pageNum) {
      this.params.pageNum = pageNum;
      this.load();
    }
  }
}
</script>
