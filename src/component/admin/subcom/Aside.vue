<template>
    <div>
      <el-menu      
      class="el-menu-vertical-demo"
      background-color="#D3DCE6"
      text-color="#000"
      active-text-color="#ffd04b">
        <!-- 预留一个一级菜单, 将来通过v-for动态生成多组一级菜单 -->
        <!-- 这里的index用来给当前菜单起个名字, 以区分 -->
      <el-submenu  v-for="item in menu" :key="item.title"  :index="item.title">
         <!-- 菜单title --> 
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>{{item.title}}</span>
        </template>
      <!-- 菜单list, 遍历当前菜单的chidren拿数据 -->
      <el-menu-item :index="subitem.title" v-for="subitem in item.children" :key="subitem.title">
          <router-link :to="subitem.path">{{subitem.title}}</router-link>
      </el-menu-item>
      </el-submenu>
      


    </el-menu>
  
    </div>
</template>

<script>
    export default {
        data() {
            return{
                  // 左侧导航列表数据
                  menu:[
                      {
                          title:'商品管理',
                          children:[
                              { title:'内容管理',path:'/admin/goods/list'},
                              { title: '类别管理', path: '/admin/goods/category'},
                              { title: '评论管理', path: '/admin/goods/comment'} 
                          ] 
                      },
                      {
                          title: '订单管理',  
                            children:[
                              { title:'内容管理',path:'/admin/a'},
                              { title: '类别管理', path: '/admin/b'},
                              { title: '评论管理', path: '/admin/c'} 
                          ] 
                      }
                  ]
            }
        }


    }
</script>

<style scoped>

</style> 