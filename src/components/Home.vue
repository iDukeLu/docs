<template>
  <div class="main_container">
    <el-container style="height: 100%; width: 100%; border: 1px solid #eee">
      <!-- 左侧菜单 -->
      <el-aside class="menu">
        <el-menu :collapse="isCollapse" background-color="#545c64" text-color="#fff" active-text-color="#ffd04b" style="height: 100%; width: 100%" @open="handleOpen" @close="handleClose">

          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-collection"/>
              <span slot="title">系统管理</span>
            </template>
            <el-menu-item-group>
              <el-menu-item index="1-1">服务管理</el-menu-item>
              <el-menu-item index="1-2">接口设计</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
        </el-menu>
      </el-aside>
      <!-- 右侧主页 -->
      <el-container>
        <el-header>
          <template>
            <el-tabs v-model="activeName" style="padding-left: 20px" @tab-click="handleClick">
              <!-- 二级路由导航 -->
              <router-link to="/user/emails">电子邮件</router-link>
              <router-link to="/user/phones">联系方式</router-link>
              <el-tab-pane label="图书馆" name="library"/>
              <el-tab-pane label="待定。。" name="second"/>
            </el-tabs>
          </template>
        </el-header>

        <el-main>
          <!-- 二级路由展示容器 -->
          <router-view/>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
  export default {
    name: 'Home',
    data() {
      return {
        page: { // 分页
          currentPage: 1,
          pageSize: 10,
          total: 400,
          pageSizes: [10, 20, 50, 100]
        },
        book: { // 书籍
          name: '深入浅出Istio Service Mesh快速入门及实践',
          author: 'tom',
          Introduction: 'asdfaefadfasfaefaf',
          tags: ['java', 'new'],
          status: 'true' // 是否完成阅读
        },
        books: [],
        tags: ['Java', 'Python', 'Spring'],
        activeName: 'library',
        isCollapse: false
      }
    },
    methods: {
      handleOpen(key, keyPath) {
        // eslint-disable-next-line no-console
        console.log(key, keyPath)
      },
      handleClose(key, keyPath) {
        // eslint-disable-next-line no-console
        console.log(key, keyPath)
      },
      handleClick(tab, event) {
        // eslint-disable-next-line no-console
        console.log(tab, event)
      },
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  /*内容部分高度，看自己心情*/
  .main_container {
    height: 100% !important;
    width: 100% !important;
  }
  /*菜单栏*/
  .menu {
    width: 200px!important;
    background-color: rgb(238, 241, 246);
    height: 100vh;
    overflow: hidden;
  }
  .menu .el-menu-vertical{
    height: 100%;
    overflow-x: hidden;
    overflow-y: scroll;
  }
  /*菜单栏滚动条样式--宽高*/
  .menu .el-menu-vertical::-webkit-scrollbar {
    width: 8px;
    height: 8px;
  }
  /*菜单栏滚动条样式--颜色阴影圆角*/
  .menu .el-menu-vertical::-webkit-scrollbar-thumb {
    background-color:rgba(0,0,0,.05);
    border-radius: 10px;
    -webkit-box-shadow: inset 1px 1px 0  rgba(0,0,0,.1);
  }
  .el-header {
    background-color: #B3C0D1;
    color: #333;
    line-height: 60px;
  }

  .el-aside {
    color: #333;
  }
  /*右侧上方header部分去掉默认左右padding20*/
  .el-header {
    padding: 0;
  }

  .el-table-column {
    width:100px;
    white-space:nowrap;
    overflow:hidden;
    text-overflow:ellipsis;
  }
  .el-tag + .el-tag {
    margin-left: 5px;
  }

  .el-table .warning-row {
    background: red;
  }

  .el-table .success-row {
    background: green;
  }

  .el-select .el-input {
    width: 130px;
  }
  .input-with-select .el-input-group__prepend {
    background-color: #fff;
  }
</style>
