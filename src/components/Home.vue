<template>
  <div>
    <header class="bg-dark">
      <div class="container">
        <nav class="navbar navbar-expand-md no-gutters">
          <div class="col-3 text-left">
            <span> {{sysName}} </span>
          </div>

          <button class="navbar-toggler" type="button" data-toggle="collapse" data-target=".navbar-collapse-4" aria-controls="navbarNav7" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>

          <div class="collapse navbar-collapse navbar-collapse-4 justify-content-center col-md-6" id="navbarNav7">
            <ul class="navbar-nav justify-content-center">
              <template v-for="(item,index) in $router.options.routes" v-if="!item.hidden">
                <b-nav-item-dropdown :text="item.name">
                  <b-dropdown-item v-for="child in item.children" :href="child.path" v-if="!child.hidden" :index="child.path" :key="child.path">{{child.name}}</b-dropdown-item>
                </b-nav-item-dropdown>
              </template>
            </ul>
          </div>

          <div class="collapse navbar-collapse navbar-collapse-4">
            <b-navbar-nav class="ml-auto">
              <b-nav-item-dropdown right>
                <!-- Using button-content slot -->
                <template slot="button-content">
                  <span class="rounded-circle">
                    <b-img src="sysUserAvatar" rounded="circle" blank width="30" height="30" blank-color="#777" alt="img" class="m-1"/>{{sysUserName}}
                  </span>
                </template>
                <b-dropdown-item href="#">My Message</b-dropdown-item>
                <b-dropdown-item href="#">Settings</b-dropdown-item>
              </b-nav-item-dropdown>
              <b-nav-item @click="logout">Logout</b-nav-item>
            </b-navbar-nav>
          </div>
        </nav>
      </div>
    </header>
    
    <section class="fdb-block">
      <div class="container">
        <div class="row justify-content-center">
          <div class="col col-md-8 text-center">
            <transition name="fade" mode="out-in">
              <router-view></router-view>
            </transition>
          </div>
        </div>
      </div>
    </section>

    <footer class="fdb-block footer-small bg-dark">
      <div class="container">
        <div class="row align-items-center">
          <div class="col-12 col-md-8">
            <ul class="nav justify-content-center justify-content-md-start">
              <li class="nav-item">
                <a class="nav-link active" href="#">Home</a>
              </li>
            </ul>
          </div>
          <div class="col-12 col-md-4 mt-4 mt-md-0 text-center text-md-right">
            &copy; 2017 {{sysName}}. All Rights Reserved
          </div>
        </div>
      </div>
    </footer>
  </div>
  <!-- <el-row class="container">
    <el-col :span="24" class="main">
      <aside :class="collapsed?'menu-collapsed':'menu-expanded'">
        <el-menu :default-active="$route.path" class="el-menu-vertical-demo" @open="handleopen" @close="handleclose" @select="handleselect"
           unique-opened router v-show="!collapsed">
          
          <template v-for="(item,index) in $router.options.routes" v-if="!item.hidden">
            
            <el-submenu :index="index+''" v-if="!item.leaf">
              <template slot="title"><i :class="item.iconCls"></i>{{item.name}}</template>
              <el-menu-item v-for="child in item.children" :index="child.path" :key="child.path" v-if="!child.hidden">{{child.name}}</el-menu-item>
            </el-submenu>
            
            <el-menu-item v-if="item.leaf&&item.children.length>0" :index="item.children[0].path"><i :class="item.iconCls"></i>{{item.children[0].name}}</el-menu-item>
          
          </template>
        
        </el-menu>
        
      </aside>
    </el-col>
  </el-row> -->
</template>

<script>
  export default {
    data () {
      return {
        sysName: 'VUEADMIN',
        collapsed: false,
        sysUserName: '',
        sysUserAvatar: '',
        form: {
          name: '',
          region: '',
          date1: '',
          date2: '',
          delivery: false,
          type: [],
          resource: '',
          desc: ''
        }
      }
    },
    methods: {
      onSubmit () {
        console.log('submit!')
      },
      handleopen () {
      },
      handleclose () {
      },
      handleselect: function (a, b) {
      },
      logout: function () {
        sessionStorage.removeItem('user')
        this.$router.push('/login')
      }
    },
    mounted () {
      var user = sessionStorage.getItem('user')
      if (user) {
        user = JSON.parse(user)
        this.sysUserName = user.name || ''
        this.sysUserAvatar = user.avatar || ''
      }
    }
}
</script>
<style scoped>
footer {
  position: absolute;
  bottom: 0;
  width:100%;
}
</style>