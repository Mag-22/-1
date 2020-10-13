<template>
  <div>
    <template v-for="item in this.MenuList">
      <el-submenu :disabled="item.disabled" :index="item.id+''" :key="item.id+''" v-if="item.children.length>0">
                    <template slot="title" style="padding-left=60px">
                      <i :class="item.icon"></i>
                      <span slot="title">{{item.menuName}}</span>
                    </template>
                    <MenuTree :MenuList="item.children"></MenuTree>
      </el-submenu>
      <el-menu-item
      v-else
      :disabled="item.disabled"
      :index="item.url+''"
      :route="item.url+''"
      :key="item.id"
      @click="savePath(item.url)"
      style="padding-left:50px;"
      >
        <i :class="item.icon"></i>
        <span slot="title">{{item.menuName}}</span>
      </el-menu-item>
    </template>
  </div>
</template>
<script>
export default {
  name: 'MenuTree',
  props: ['MenuList']
}
</script>
<style scoped>
    .el-menu--collapse span,
    .el-menu--collapse i.el-submenu__icon-arrow
    {  height: 0;
      width: 0;  overflow: hidden;  visibility: hidden;  display: inline-block; }
    .el-submenu__title {
         font-size: 14px;
         color: #303133;
         padding: 0 60px;
         cursor: pointer;
         transition: border-color .3s,background-color .3s,color .3s;
         box-sizing: border-box;
     }
</style>
