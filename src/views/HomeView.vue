<template>
  <div>
    <!-- 搜索 -->
    <header style="margin-bottom: 20px;">
      <el-input placeholder="请输入名称" style="width: 240px;"></el-input>
      <el-input placeholder="请输入联系方式" style="width: 240px; margin-left: 5px;"></el-input>
      <el-button type="primary" style="margin-left: 5px;"><i class="el-icon-search"></i> 搜索</el-button>
    </header>

    <el-table :data="tableData" stripe>
      <el-table-column prop="name" label="名称"></el-table-column>
      <el-table-column prop="age" label="年龄"></el-table-column>
      <el-table-column prop="address" label="地址"></el-table-column>
      <el-table-column prop="phone" label="电话"></el-table-column>
      <el-table-column prop="sex" label="性别"></el-table-column>
    </el-table>

    <el-pagination
      style="margin-top: 20px;"
      background
      layout="prev, pager, next"
      :page-size="5"
      :total="tableData.length">
    </el-pagination>
  </div>
</template>

<script>

export default {
  name: 'HomeView',
  data() {
    return {
      tableData: [
        {name: '王五', age: 20, address: '北京市', phone: '13583483454', sex: '男'},
        {name: '王五', age: 20, address: '北京市', phone: '13583483454', sex: '男'},
        {name: '王五', age: 20, address: '北京市', phone: '13583483454', sex: '男'},
        {name: '王五', age: 20, address: '北京市', phone: '13583483454', sex: '男'},
      ]
    }
  }
}
</script>
