<template>
<!-- Login Form -->
<div class="container-fluid">
      <div class="row">


<div class="d-sm-none d-md-block col-md-4 ">1</div>
<div class="col-sm-12 col-md-4 col-xl-4">
    <form class="formulario">
        <input type="text" name="login" placeholder="Gmail" v-model="usuario">
        <input type="text" name="login" placeholder="Contraseña" v-model="password">
        <input type="submit"  value="Log In">
    </form>
</div>
<div class="d-sm-none d-md-block ">3</div>
 </div>

 </div>

                
    
</template>

<script>


</script>

<style scoped>

.formulario{
 display: flex;
 justify-content: center;
 flex-direction: column;
}

.spaced {
    width: 100vw;
    
}
</style>
