<template>
<div class="container-fluid">
    <form class="row" >

        <div class="form-group">
            <label >Email:</label>
            <input type="email" class="form-control" placeholder="ingresa tu email" v-model="email">
        </div>

        <div class="form-group">
            <label >Contraseña:</label>
            <input type="password" class="form-control" placeholder="ingresa tu contraseña" v-model="password" >
        </div>

        <button class="btn btn-warning" @click.prevent="validation()">
            Login
        </button>
    </form>
</div>
</template>

<script>

export default {
    name: 'Login',

    data(){
        return{
            loginData: [],
            email: "",
            password:"",
        }
    },
    
    methods: {
        validation(){
            if(this.loginData[0].password === this.password && this.loginData[0].email === this.email){
                console.log("login")
                this.$router.push("/home")
            }else{
                alert("El email y/o la contraseña son incorrectos")
            }
        }
    },

    async mounted(){
    try{
      const respuesta = await fetch("json/auth.json");
      const datosAuth = await respuesta.json();
      this.loginData = datosAuth.data
      
    }catch(error){
      console.log(error.message);
    }
}
}
</script>

<style scoped>
    *{
         background-color:darkgray;        
     }
    

</style>

