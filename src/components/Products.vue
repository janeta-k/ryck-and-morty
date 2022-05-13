<template>
<div class="container mb-5">

    <button 
  type="button"
  class="btn btn-outline-info btn-lg boton-nav"
  data-bs-toggle="modal"
  data-bs-target="#verCarrito"
  >
  Ver tu carrito
  </button>
   
<!--buscador-->
  <div class="row">   
    <div class="d-flex justify-content-center mb-4 mt-4">
      <input  type="search" v-model="buscar" placeholder="Busca un Personaje" aria-label="Search" >
      <button class="btn btn-outline-success" type="submit">Buscar</button>
    </div>
  </div>

<!--
{{items}}
-->


<!--cards-->
  
    <div class="row justify-content-center">
      <div
        class="card col-6 col-sm-3 m-3 p-0"
        v-for="(item, index) in items"
        :key="index"
      >
        <img
          class="card-img-top"
          v-bind:src="item.image"
          v-bind:alt="item.name"
        />
        <div class="card-body">
          <h5 class="card-title">{{ item.name }}</h5>
          <p class="card-text">Origen: {{ item.origin.name }}</p>
          <p class="card-text">Estado: {{ item.status }}</p>
          <button type="button" class="btn btn-primary " data-bs-toggle="modal" data-bs-target="#exampleModal" @click="showMore(item)" >
              Ver detalles
          </button>
         <a href="#" class="card-button btn btn-primary" @click="addToCart(item)">Agregar al carrito</a>
        </div>
      </div>
    </div>

     <!-- Modal  de ver detalles-->
<div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true" >
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel" >{{modal.name}}</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body" >
        <ul>
          <li>Orígen: {{modal.origin}}</li>
          <li>Estado: {{modal.status}}</li>
          <li>Género: {{modal.gender}}</li>
        </ul>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
      </div>
    </div>
  </div>
</div>

<CartDetail :modalCart="carrito"/>
  </div>
</template>

<script>
//import de json ejemplo buscador en tiempo real
//import datos from '../assets/json/ryckAndMorty.json'

import CartDetail from '@/components/CartDetail.vue'



export default {
  
  name: 'Products',

  components:{
    CartDetail
  },


  data() {
    return {
      
      personajes:[],

      carrito:[],

      buscar: "",

      modal:{
        name: "",
        origin: "",
        status:"",
        gender:""
      },

      modalCart:{
        name:'',
        cantidad:'',
      },

    };
    
    
  },

  created(){
   fetch("json/ryckAndMorty.json")
   .then(response => response.json())
   .then(datos => this.personajes = datos.characters)
  },

  methods:{

    //método para el modal "ver detalles"
    showMore(object){
     //this.modal.title = object.name
      this.modal = {
       name: object.name,
       origin:object.origin.name,
       status:object.status,
       gender:object.gender,
      }
     console.log(object)
    },

   //método para agregar al carrito y aumentar la cantidad del producto
    addToCart(object){
     let personajes = this.personajes.find(item => item==object)
     let booleano = this.carrito.some(item => item == object)

      if(booleano){
        console.log(personajes.cantidad += 1) 
        console.log(personajes.cantidad)
      }else{
        console.log(this.carrito.push(personajes))
        console.log(this.carrito)
      }
    },

//método para disminuir la cantidad 
/*
    disminuir(elemento){
      let personajes = this.personajes.find(item => item == elemento)
     let booleano = this.carrito.some(item => item == elemento)

     if(booleano){
       return personajes.cantidad -= 1
     }
     
    },
*/
    
  },

  computed: {
    //método para el buscador en tiempo real
    items() {
      return this.personajes.filter(item => {
        return item.name.toLowerCase().includes(this.buscar.toLowerCase());
      });
    },
  },

};
</script>

<style scoped>

</style>