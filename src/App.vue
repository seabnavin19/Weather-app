<template>
  <div>
    <Navbar/>
    <router-view></router-view>
  </div>
 
</template>
<script>
import Navbar from "./components/Navbar"
import  "../node_modules/bootstrap/dist/css/bootstrap.min.css";
export default {
  name: "app",
  components:{
    Navbar
  },
  

}
</script>