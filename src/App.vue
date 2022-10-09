<template>
  <div id="app">
    <!-- 头部 -->
    <header class="header">
      <img src="@/assets/logo.png" alt="" class="logo">
      <span class="title">图书管理系统</span>
    </header>

    <div style="display: flex;">
      <!-- 侧边栏 -->
      <aside class="aside">
        <el-menu :default-active="$route.path" router :default-openeds="['/']" class="el-menu-demo">
          <el-menu-item index="/">
            <i class="el-icon-eleme"></i>
            <span>首页</span>
          </el-menu-item>
          <el-submenu index="/">
            <template slot="title">
              <i class="el-icon-question"></i>
              <span>关于页面</span>
            </template>
            <el-menu-item index="about">关于详情</el-menu-item>
          </el-submenu>
        </el-menu>
      </aside>
      <!-- 主体 -->
      <main class="main">
        <router-view/>
      </main>
    </div>
  </div>
</template>

<style>
.header {
  height: 60px;
  line-height: 60px;
  background-color: #fff;
  margin-bottom: 2px;
}
.logo {
  width: 40px;
  position: relative;
  top: 10px;
  left: 20px;
}
.title {
  margin-left: 25px;
  font-size: 24px;
}
.aside {
  width: 200px;
  overflow: hidden;
  margin-right: 2px;
  background-color: #fff;
  min-height: calc(100vh - 62px);
}
.main {
  flex: 1;
  background-color: #fff;
  padding: 10px;
}
</style>