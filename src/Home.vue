<template>
  <el-container class="home-container">
    <el-header height="100px">
      <div class="logo-box">logo</div>
      <div class="status-box">status</div>
    </el-header>
    <el-container>
      <el-aside width="200px">Aside</el-aside>
      <el-main>Main</el-main>
    </el-container>
  </el-container>
</template>

<script>
export default {
  name: 'Home'
}
</script>

<style scoped>
.home-container {
  width: 100%;
  height: 100%;
}

.el-header {
  background-color: #4ca2cd;
  color: #333;
  text-align: center;
  position: relative;
  line-height: 100px;
}

.logo-box {
  position: absolute;
  left: 0;
  top: 0;
  width: 200px;
  height: inherit;
}

.status-box {
  position: absolute;
  right: 0;
  top: 0;
  width: 200px;
  height: inherit;
}

.el-aside {
  background-color: #01233E;
  color: #333;
  text-align: center;
  line-height: 200px;
}

.el-main {
  background-color: #E9EEF3;
  color: #333;
  text-align: center;
  line-height: 160px;
}
</style>
