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
          <p class="card-text">{{item.stock}}</p>
          <p class="card-text" v-if="item.stock>5">En stock</p>
          <p class="card-text" v-else-if="item.stock<=5 && item.stock>0">¡Queda poco stock!</p>
          <p class="card-text" v-else>sin stock</p>

          <button type="button" class="btn btn-primary " data-bs-toggle="modal" data-bs-target="#exampleModal" @click="showMore(item)" >
            Ver detalles
          </button>

          <button href="#" class="card-button btn btn-primary" v-if="item.stock>0" @click="addToCart(item); reduceStock(item)">Agregar al carrito</button>
          <button href="#" class="card-button btn btn-primary disabled" v-else-if="item.stock<=0" @click="addToCart(item); reduceStock(item)">Agregar al carrito</button>
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

<CartDetail :modalCart="carrito" :totalCart="precioTotal" @click1="disminuir" @click2="aumentar" @click3="quitar" @vaciar ="vaciarCart" @reduceStock="dropStockCart"/>
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
      precioTotal: 0,
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

  async created(){
    try{
      const respuesta = await fetch("json/ryckAndMorty.json");
      const datosApi = await respuesta.json();
      this.personajes = datosApi.characters

    }catch(error){
      console.log(error.message);
    }
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

    //método para agregar los personajes al carrito y aumentar la cantidad del producto
    addToCart(object){
     let personajes = this.personajes.find(item => item == object)
     let booleano = this.carrito.some(item => item == object)

      if(booleano){
        console.log(personajes.cantidad += 1) 
        console.log(personajes.cantidad)
      }else{
        console.log(this.carrito.push(personajes))
        console.log(this.carrito)
      }
      this.precio()
    },

    /* --- métodos para stock ---*/

    //método para descontar stock onclick de card "items"
    reduceStock(stock){
      let stockPersonajes = this.personajes.find(item => item == stock)      
      stockPersonajes.stock--
    },

    //método para descontar stock "carrito"
    dropStockCart(elemento){
      let stockCarrito = this.carrito.find(item => item == elemento)
      stockCarrito.stock--
    },

  /* --- Métodos para el carrito --- */

    //método para disminuir la cantidad de productos (-) y restaurar el stock de este
    disminuir(elemento){
      let personajes = this.personajes.find(item => item == elemento)
      personajes.cantidad--

      let stockCarrito = this.carrito.find(item => item == elemento)
      stockCarrito.stock++
      
        if(personajes.cantidad < 1){
          personajes.cantidad = 1
          stockCarrito.stock = 12
          this.quitar(elemento)
        }
      
      this.precio()
    },

    //método para aumentar la cantidad (+)
    aumentar(elemento){
      let personajesCarrito = this.carrito.find(item => item == elemento)
      personajesCarrito.cantidad++
      this.precio()
    },

    //método para quitar los productos (x)
    quitar(elemento){
      let index = this.carrito.findIndex(item => item == elemento);
      this.carrito.splice(index, 1);
      this.precio()
    },

    //método para calcular el precio total
    precio(){
      this.precioTotal = 0
      for (let i=0; i<this.carrito.length; i++){
      this.precioTotal += this.carrito[i].precio*this.carrito[i].cantidad;
      }
    },

    //método para vaciar el carrito
    vaciarCart(){
      this.carrito = []
      this.precio()
    },
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