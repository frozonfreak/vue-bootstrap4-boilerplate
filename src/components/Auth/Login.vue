<template>
  <div>
    <section class="fdb-block">
      <div class="container">
        <div class="row justify-content-end">
          <div class="col-12 col-md-8 col-lg-6 col-xl-5 text-left">
            <div class="fdb-box">
              <div class="row">
                <div class="col">
                  <h1>Log In</h1>
                  <p class="text-h3">Right at the coast of the Semantics, a large language ocean. A small river named Duden.</p>
                </div>
              </div>
              <div class="row">
                <div class="col mt-4">
                  <input type="text" class="form-control" placeholder="Email" v-model="ruleForm2.account">
                </div>
              </div>
              <div class="row mt-4">
                <div class="col">
                  <input type="password" class="form-control" placeholder="Password" v-model="ruleForm2.checkPass">
                </div>
              </div>
              <div class="row mt-4">
                <div class="col">
                  <button class="btn" type="button"  @click.native.prevent="handleSubmit">Submit</button>
                  <button class="btn" type="button" @click.native.prevent="handleReset">Reset</button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
  import { requestLogin } from '../../api/api'
  import NProgress from 'nprogress'
  export default {
    data () {
      return {
        loading: false,
        ruleForm2: {
          account: 'admin',
          checkPass: '123456'
        },
        checked: true
      }
    },
    methods: {
      handleReset () {
        this.ruleForm2.account = ''
        this.ruleForm2.checkPass = ''
      },
      handleSubmit (ev) {
        console.log('clcked')
        // var _this = this
        // _this.$router.replace('/helloworld')
        this.loading = true
        NProgress.start()
        var loginParams = { username: this.ruleForm2.account, password: this.ruleForm2.checkPass }
        requestLogin(loginParams).then(data => {
          this.loading = false
          NProgress.done()
          let { msg, code, user } = data
          if (code !== 200) {
            this.$message({
              message: msg,
              type: 'error'
            })
          } else {
            sessionStorage.setItem('user', JSON.stringify(user))
            this.$router.push({ path: '/helloworld' })
          }
        })
      }
    }
  }
</script>
<style scoped>
  .fdb-block {
    background-image: url("data:image/svg+xml;charset=UTF-8,%3csvg xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink' width='3000' height='2000' viewBox='0 0 3000 2000'%3e%3cmetadata%3e%3c?xpacket begin=' ' id='W5M0MpCehiHzreSzNTczkc9d'?%3e%3cx:xmpmeta xmlns:x='adobe:ns:meta/' x:xmptk='Adobe XMP Core 5.6-c138 79.159824, 2016/09/14-01:09:01 '%3e%3crdf:RDF xmlns:rdf='http://www.w3.org/1999/02/22-rdf-syntax-ns%23'%3e%3crdf:Description rdf:about=''/%3e%3c/rdf:RDF%3e%3c/x:xmpmeta%3e%3c?xpacket end='w'?%3e%3c/metadata%3e%3cdefs%3e%3cstyle%3e .cls-1 %7b fill: url(%23linear-gradient);%7d .cls-2, .cls-3 %7b fill: %23fff; fill-rule: evenodd;%7d .cls-2 %7b opacity: 0.25;%7d .cls-3 %7b opacity: 0.2;%7d %3c/style%3e%3clinearGradient id='linear-gradient' x1='1495' y1='2018' x2='1495' y2='-31' gradientUnits='userSpaceOnUse'%3e%3cstop offset='0' stop-color='%23644aea'/%3e%3cstop offset='1' stop-color='%23ac65ca'/%3e%3c/linearGradient%3e%3c/defs%3e%3crect class='cls-1' x='-38' y='-31' width='3066' height='2049'/%3e%3cpath id='Color_Fill_1' data-name='Color Fill 1' class='cls-2' d='M-53,1148c79.185-64.07,227.883,59.4,288,25,859.29-491.76,767.66,18.19,1006-72,309.84-117.249,403.57,203.75,770,79,254.89-86.78,741.48-353.2,989-293,107.71,26.2,0,1300,0,1300H-2C-1.235,2186.42-61.021,1187.41-53,1148Z'/%3e%3cpath id='Color_Fill_2' data-name='Color Fill 2' class='cls-3' d='M-2,840c457.748,14.672,551.1,278.46,820,261,253.51-16.46,434.71-181.553,689-165,328.14,21.36,413.1,72.01,800,84,597.49,18.51,599.28-61.959,694-102,172.94-73.109,0,1269,0,1269L-5,2181C-4.234,2180.42-10.021,879.409-2,840Z'/%3e%3c/svg%3e ");
  }
</style>
