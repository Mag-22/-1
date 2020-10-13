<template>
  <el-container class="main_container">
  <!--头部布局-->
    <el-header>
      <div class="left_box">
         <img src="../assets/img/0.png">
         <span>物资管理系统</span>
      </div>
      <div class="right_box">
        <el-dropdown>
          <img src="../assets/img/1.gif">
          <span class="el-dropdown-link">
               <i class="el-icon-arrow-down el-icon--right"></i>
          </span>
          <el-dropdown-menu slot="dropdown">
            <el-dropdown-item icon="el-icon-house">系统首页</el-dropdown-item>
            <el-dropdown-item icon="el-icon-ship">交流讨论</el-dropdown-item>
            <el-dropdown-item icon="el-icon-switch-button">退出登录</el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>
      </div>
    </el-header>
    <el-container>
    <!--侧边栏-->
      <el-aside :width="isCollapse?'60px':'200px'">
      <div class="toggle_box" @click="toggleCollapse">|||</div>
       <el-menu
            default-active="2"
            class="el-menu-vertical-demo"
            @open="handleOpen"
            @close="handleClose"
            background-color="#001529"
            text-color="#fff"
            active-text-color="ffd04b"
            :collapse="isCollapse"
            :collapse-transition="false"
            :unique-opened="true"
            :router="true">
             <MenuTree :MenuList="this.MenuList"></MenuTree>
          </el-menu>
      </el-aside>
      <el-main>
        <!--路由视图-->
        <router-view></router-view>
      </el-main>
    </el-container>
  </el-container>
</template>

<script>
import MenuTree from '../components/MenuTree'
export default {
  name: 'Main',
  data () {
    return {
      isCollapse: false,
      MenuList: [
        {
          id: 1,
          parentId: 0,
          menuName: '系统管理',
          url: '',
          icon: 'el-icon-setting',
          orderNum: 1,
          open: 1,
          disabled: false,
          perms: null,
          type: 0,
          children: [
            {
              id: 253,
              parentId: 1,
              menuName: '欢迎页面',
              url: '/welcome',
              icon: 'el-icon-star-off',
              orderNum: 1,
              open: 0,
              disabled: false,
              perms: 'welcome:view',
              type: 0,
              children: []
            },
            {
              id: 226,
              parentId: 1,
              menuName: '用户管理',
              url: '/users',
              icon: 'el-icon-user',
              orderNum: 2,
              open: 0,
              disabled: false,
              perms: 'users',
              type: 0,
              children: []
            },
            {
              id: 235,
              parentId: 1,
              menuName: '角色管理',
              url: '/roles',
              icon: 'el-icon-postcard',
              orderNum: 3,
              open: 0,
              disabled: false,
              perms: '',
              type: 0,
              children: []
            },
            {
              id: 261,
              parentId: 1,
              menuName: '部门管理',
              url: '/departments',
              icon: 'el-icon-s-home',
              orderNum: 3,
              open: 0,
              disabled: false,
              perms: '',
              type: 0,
              children: []
            },
            {
              id: 319,
              parentId: 1,
              menuName: '公告管理',
              url: '/notices',
              icon: 'el-icon-s-flag',
              orderNum: 4,
              open: 0,
              disabled: true,
              perms: '',
              type: 0,
              children: []
            }]
        },
        {
          id: 312,
          parentId: 0,
          menuName: '业务管理',
          url: null,
          icon: 'el-icon-s-goods',
          orderNum: 2,
          open: 0,
          disabled: false,
          perms: null,
          type: 0,
          children: [
            {
              id: 229,
              parentId: 312,
              menuName: '物资管理',
              url: '',
              icon: 'el-icon-date',
              orderNum: 1,
              open: 1,
              disabled: false,
              perms: 'el-icon-date',
              type: 0,
              children: [
                {
                  id: 230,
                  parentId: 229,
                  menuName: '物资入库',
                  url: '/inStocks',
                  icon: 'el-icon-date',
                  orderNum: 1,
                  open: 1,
                  disabled: false,
                  perms: 'el-icon-date',
                  type: 0,
                  children: []
                },
                {
                  id: 267,
                  parentId: 229,
                  menuName: '物资资料',
                  url: '/products',
                  icon: 'el-icon-goods',
                  orderNum: 2,
                  open: 0,
                  disabled: false,
                  perms: '',
                  type: 0,
                  children: []
                },
                {
                  id: 268,
                  parentId: 229,
                  menuName: '物资类别',
                  url: '/productCategorys',
                  icon: 'el-icon-star-off',
                  orderNum: 2,
                  open: 0,
                  disabled: false,
                  perms: '',
                  type: 0,
                  children: []
                },
                {
                  id: 270,
                  parentId: 229,
                  menuName: '物资发放',
                  url: '/outStocks',
                  icon: 'el-icon-goods',
                  orderNum: 5,
                  open: 1,
                  disabled: false,
                  perms: '',
                  type: 0,
                  children: []
                },
                {
                  id: 316,
                  parentId: 229,
                  menuName: '物资库存',
                  url: '/stocks',
                  icon: 'el-icon-tickets',
                  orderNum: 5,
                  open: 0,
                  disabled: false,
                  perms: '',
                  type: 0,
                  children: []
                }]
            },
            {
              id: 311,
              parentId: 312,
              menuName: '物资流向',
              url: null,
              icon: 'el-icon-edit',
              orderNum: 3,
              open: 0,
              disabled: false,
              perms: null,
              type: 0,
              children: [
                {
                  id: 310,
                  parentId: 311,
                  menuName: '物资去处',
                  url: '/consumers',
                  icon: 'el-icon-edit',
                  orderNum: 1,
                  open: 0,
                  disabled: false,
                  perms: '',
                  type: 0,
                  children: []
                },
                {
                  id: 269,
                  parentId: 311,
                  menuName: '物资来源',
                  url: '/suppliers',
                  icon: 'el-icon-coordinate',
                  orderNum: 5,
                  open: 0,
                  disabled: false,
                  perms: '',
                  type: 0,
                  children: []
                }]
            }]
        },
        {
          id: 295,
          parentId: 0,
          menuName: '其他管理',
          url: '',
          icon: 'el-icon-s-marketing',
          orderNum: 5,
          open: 0,
          disabled: false,
          perms: '',
          type: 0,
          children: [

            {
              id: 341,
              parentId: 295,
              menuName: 'QQ交流群',
              url: '/blog',
              icon: 'el-icon-view',
              orderNum: 1,
              open: 0,
              disabled: false,
              perms: '',
              type: 0,
              children: []
            },
            {
              id: 318,
              parentId: 295,
              menuName: '图标管理',
              url: '/icons',
              icon: 'el-icon-star-off',
              orderNum: 2,
              open: 1,
              disabled: false,
              perms: '',
              type: 0,
              children: []
            }]
        },
        {
          id: 5,
          parentId: 0,
          menuName: '日志管理',
          url: '/logs',
          icon: 'el-icon-camera',
          orderNum: 6,
          open: 0,
          disabled: false,
          perms: null,
          type: 0,
          children: [
            {
              id: 271,
              parentId: 5,
              menuName: '登入日志',
              url: '/loginLog',
              icon: 'el-icon-date',
              orderNum: 1,
              open: 0,
              disabled: false,
              perms: 'login:log',
              type: 0,
              children: []
            },
            {
              id: 307,
              parentId: 5,
              menuName: '操作日志',
              url: '/logs',
              icon: 'el-icon-edit',
              orderNum: 1,
              open: 1,
              disabled: false,
              perms: '',
              type: 0,
              children: []
            }]
        }]
    }
  },
  components: {
    MenuTree
  },
  methods: {
    toggleCollapse () {
      this.isCollapse = !this.isCollapse
    }
  }
}
</script>

<style lang="less" scoped>
   .main_container{
       height:100%;
       }
    /*头部布局*/
   .el-header {
       background-color: #001529;
       display:flex;
       justify-content:space-between;
       padding-left:0;
       color: #ffffff;
       align-items: center;
       font-size:20px;
       .left_box{
          background-color: #001529;
          display:flex;
          align-items:center;
          img{
             width:60px;
             height:60px;
             margin:0,0,10px,15px;
          }
          span{
             margin-left:15px;
          }
       }
       .right_box{
          .el-dropdown>img{
                                     width:60px;
                                     height:60px;
                                     border-radius:50%;
                                     background-color:#ffffff;
                                     margin:0px -45px 0px 0px;

                     }
       }
     }
     /*侧边栏*/
     .el-aside {
       background-color: #001529;
       text-align: center;
       .el-menu{
         border-right:none;
       }
       .toggle_box{
          background-color:pink;
          font-size:15px;
          font-weight:bold;
          font-height:24px;
          color:#ffffff;
          letter-spacing:0.2em;
          text-align:center;
          cursor:pointer;
       }
     }
     /*内容主体*/
     .el-main {
       background-color: #E9EEF3
     }

     body > .el-container {
       margin-bottom: 40px;
     }
     .el-dropdown-link {
        cursor: pointer;
        color: #409EFF;
      }
      /*下拉菜单样式*/
      .el-icon-arrow-down {
        font-size: 20px;
      }
      .demonstration{
       display:block;
       color:#8492a6;
       font-size:14px;
       margin-bottom:20px;
      }
</style>
