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
              <li class="nav-item active">
                <a class="nav-link" href="https://www.froala.com">Home <span class="sr-only">(current)</span></a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="https://www.froala.com">Features</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="https://www.froala.com">Pricing</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="https://www.froala.com">Team</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="https://www.froala.com">Contact</a>
              </li>
            </ul>
          </div>

          <div class="collapse navbar-collapse navbar-collapse-4">
            <ul class="navbar-nav ml-auto justify-content-end">
              <li class="nav-item">
                <a class="nav-link" href="https://www.froala.com">Log In</a>
              </li>
            </ul>

            <a class="btn ml-md-3" href="https://www.froala.com">Register</a>
          </div>
        </nav>
      </div>
    </header>
    
    <transition name="fade" mode="out-in">
      <router-view></router-view>
    </transition>

    <footer class="fdb-block footer-small bg-dark">
      <div class="container">
        <div class="row align-items-center">
          <div class="col-12 col-md-8">
            <ul class="nav justify-content-center justify-content-md-start">
              <li class="nav-item">
                <a class="nav-link active" href="https://www.froala.com">Home</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="https://www.froala.com">Features</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="https://www.froala.com">Terms</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="https://www.froala.com">About</a>
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
    <el-col :span="24" class="header">
      <el-col :span="10" class="logo" :class="collapsed?'logo-collapse-width':'logo-width'">
        {{collapsed?'':sysName}}
      </el-col>
      <el-col :span="10">
        <div class="tools" @click.prevent="collapse">
          <i class="fa fa-align-justify"></i>
        </div>
      </el-col>
      <el-col :span="4" class="userinfo">
        <el-dropdown trigger="hover">
          <span class="el-dropdown-link userinfo-inner"><img :src="this.sysUserAvatar" /> {{sysUserName}}</span>
          <el-dropdown-menu slot="dropdown">
            <el-dropdown-item>My Message</el-dropdown-item>
            <el-dropdown-item>Settings</el-dropdown-item>
            <el-dropdown-item divided @click.native="logout">Logout</el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>
      </el-col>
    </el-col>

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
        
        <ul class="el-menu el-menu-vertical-demo collapsed" v-show="collapsed" ref="menuCollapsed">
          <li v-for="(item,index) in $router.options.routes" v-if="!item.hidden" class="el-submenu item">
            <template v-if="!item.leaf">
              <div class="el-submenu__title" style="padding-left: 20px;" @mouseover="showMenu(index,true)" @mouseout="showMenu(index,false)"><i :class="item.iconCls"></i></div>
              <ul class="el-menu submenu" :class="'submenu-hook-'+index" @mouseover="showMenu(index,true)" @mouseout="showMenu(index,false)"> 
                <li v-for="child in item.children" v-if="!child.hidden" :key="child.path" class="el-menu-item" style="padding-left: 40px;" :class="$route.path==child.path?'is-active':''" @click="$router.push(child.path)">{{child.name}}</li>
              </ul>
            </template>
            <template v-else>
              <li class="el-submenu">
                <div class="el-submenu__title el-menu-item" style="padding-left: 20px;height: 56px;line-height: 56px;padding: 0 20px;" :class="$route.path==item.children[0].path?'is-active':''" @click="$router.push(item.children[0].path)"><i :class="item.iconCls"></i></div>
              </li>
            </template>
          </li>
        </ul>
      </aside>
      <section class="content-container">
        <div class="grid-content bg-purple-light">
          <el-col :span="24" class="breadcrumb-container">
            <strong class="title">{{$route.name}}</strong>
            <el-breadcrumb separator="/" class="breadcrumb-inner">
              <el-breadcrumb-item v-for="item in $route.matched" :key="item.path">
                {{ item.name }}
              </el-breadcrumb-item>
            </el-breadcrumb>
          </el-col>
          <el-col :span="24" class="content-wrapper">
            <transition name="fade" mode="out-in">
              <router-view></router-view>
            </transition>
          </el-col>
        </div>
      </section>
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
        var _this = this
        this.$confirm('Confirm Exit?', 'Prompt', {
        }).then(() => {
          sessionStorage.removeItem('user')
          _this.$router.push('/login')
        }).catch(() => {
        })
      },
      collapse: function () {
        this.collapsed = !this.collapsed
      },
      showMenu (i, status) {
        this.$refs.menuCollapsed.getElementsByClassName('submenu-hook-' + i)[0].style.display = status ? 'block' : 'none'
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