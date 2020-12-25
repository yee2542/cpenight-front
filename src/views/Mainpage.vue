<template>
  <div id="mainpage">
      <Navbar/>
      <h1 id="title">Mainpage</h1>
        <div class="newmain" style="margin-bottom:60px;">
            <a href="/newmain">New Main</a>
        </div>
        <div class="login">
            <a href="/login">Login</a>
        </div>
        <div class="Register">
            <a href="/register">Register</a>
        </div>
        <div class="userManagement">
            <a href="/userManagement">User Management</a>
        </div>
        <div class="souvenir">
            <a href="/souvenir">Souvenir</a>
        </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue"
export default {
    name:"mainpage",
    components:{
        Navbar
    }
}
</script>

<style scoped>
    #title{
        font-size: 30px;
        font-family: "CloudLight";
        padding-top:30px;
    }
    #mainpage{
        background: #282667;
        min-height: 100vh;
        margin-top: 0px;
    }
    a{
        color:white;
        font-size: 25px;

    }
    h1{
        margin: 0px;
    }
</style>