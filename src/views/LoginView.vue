<template>
<div class="background">
<div class="container-fluid">
    <h3 class="text-center">Login</h3>
    <Login/>
</div>
</div>
</template>


<script>
import Login from '@/components/Login.vue'

export default{
    
 components:{
     Login
    }
}
</script>

<style scoped>
   .background{
       background-color: aquamarine;
       height: 100vh;
   }    
</style>
