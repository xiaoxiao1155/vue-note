<template>
  <div id="app">
    <aside>
      <el-menu router class="el-menu-vertical" :collapse="isCollapse">
        <el-menu-item @click="toggleCollapse">
          <i :class="collapseIcon"></i>
        </el-menu-item>
        <el-menu-item index="/ClassInfo">
          <i class="el-icon-location"></i>
          <span slot="title">教室信息</span>
        </el-menu-item>
      </el-menu>
    </aside>
    <main :class="isCollapse ? 'el-menu--collapse' : ''">
      <router-view/>
    </main>
  </div>
</template>

<script>
  export default {
    name: 'App',
    computed: {
      collapseIcon() {
        return this.isCollapse ? 'el-icon-arrow-right' : 'el-icon-arrow-left';
      }
    },
    data() {
      return {
        isCollapse: true,
      }
    },
    methods: {
      toggleCollapse() {
        this.isCollapse = !this.isCollapse;
      }
    }
  }
</script>

<style lang="less">
  * {
    box-sizing: content-box;
  }
  body {
    margin: 0;
  }
  #app {
    height: 100vh;
    display: flex;
  }
  aside {
    display: inline-block;
    height: 100vh;
    & .el-menu-vertical:not(.el-menu--collapse) {
      width: 200px;
    }
  }
  main {
    display: inline-block;
    height: 100vh;
    &:not(.el-menu--collapse) {
      width: calc(100% - 200px);
    }
    &.el-menu--collapse {
      width: calc(100% - 65px);
    }
  }
</style>