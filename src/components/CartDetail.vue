<template>
 

<!-- Modal "ver carrito"-->
<div class="modal fade" id="verCarrito" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true" >
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
<!--cabecera modal-->
        <h5 class="modal-title" id="exampleModalLabel">Tu carrito</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
<!--cuerpo del modal-->
    <div class="modal-body">

    <!--card para los productos que se agregen al carrito-->
      <div class="card " v-for="(elemento, index) in modalCart" :key="index" style="width: 18rem;">

        <img src="#" class="card-img-top" alt="img">
        
        <div class="card-body">
          <h5 class="card-title">{{elemento.name}}</h5>
          <p class="card-text">{{elemento.cantidad}}</p>
          <a href="#" class="btn btn-primary" >-</a>
          <a href="#" class="btn btn-primary" >+</a>
          <a href="#" class="btn btn-primary" >x</a>
        </div>
      <!-- @click="disminuir(elemento)"  @click="aumentar(elemento)"  @click="quitar(elemento)"-->

      </div>  

    </div>

    <div class="modal-footer">
      <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
    </div>
  </div>
</div>
</div>
</template>

<script>


export default{

  name: 'CartDetail',

  props:{
    modalCart:{
      type: Array,
      required: true,
    }
  },
/*
  methods:{
    disminuir(elemento){
      let personajes = this.personajes.find(item => item == elemento)
     let booleano = this.carrito.some(item => item == elemento)

     if(booleano){
       return personajes.cantidad -= 1
     }
    },


  }
  */
}




</script>
