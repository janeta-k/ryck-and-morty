<template>
<div>
    <form >

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
                this.$router.push("/")
            }else{
                alert("El email y/o la contraseña son incorrectos")
            }
        }
    },
    mounted(){
        fetch('json/auth.json')
        .then(respuesta => respuesta.json())
        .then(datosAuth => this.loginData = datosAuth.data)
    },
}
</script>

<style scoped>
    *{background-color:darkgray}
</style>

