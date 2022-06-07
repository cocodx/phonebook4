<template>
  <div>电话簿主页</div>
</template>


<script>
  import axios from 'axios'
  import {getServerUrl} from "@/config/sys.js";

  export default {
    name:"PhoneBook",
    methods:{
      refreshToken(){
        let token = window.localStorage.getItem("token");
        axios.defaults.headers.common['token']=token
        let url = getServerUrl("/refreshToken");
        axios.get(url)
          .then(response=>{
            console.log("token刷新："+response.data.token)
            window.localStorage.setItem("token",response.data.token)
          }).catch(error=>{
          console.log(error)
        })
      },
      getPhoneBook(){
        let token = window.localStorage.getItem("token");
        axios.defaults.headers.common['token']=token
        let url = getServerUrl("phoneBook/loadAll");
        axios.get(url)
          .then(response=>{
            console.log(response)
          }).catch(error=>{
          console.log(error)
        })
      }
    },
    mounted() {
      setInterval(this.refreshToken,1000*60*10);//10分钟刷新一次
      this.getPhoneBook();
    }
  }
</script>

<style scoped>

</style>
