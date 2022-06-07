<template>
  <div>电话簿主页</div>
</template>


<script>
  import axios from 'axios'
  import {getServerUrl} from "@/config/sys.js";

  export default {
    name:"PhoneBook",
    methods:{
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
      this.getPhoneBook();
    }
  }
</script>

<style scoped>

</style>
