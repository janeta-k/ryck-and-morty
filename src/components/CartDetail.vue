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

    <!--card para los productos que se agreguen al carrito-->
    <div class="card mb-1 p-0" style="max-width: 100%;" v-for="(elemento, index) in modalCart" :key="index">
        <div class="row g-0">
          <div class="col-md-4">
            <img v-bind:src="elemento.image" class="img-fluid rounded-center">
          </div>
          <div class="col-md-8">
            <div class="card-body">
              <h5 class="card-title">{{elemento.name}}</h5>
              <p class="card-text mb-1"><strong>Cantidad:</strong> {{elemento.cantidad}}</p>
              <p class="card-text mb-2"><strong>Precio c/u:</strong> ${{elemento.precio}}</p>
              <div class="btn-group" role="group" aria-label="Basic example">
              <button href="#" class="btn btn-primary" @click="disminuir(elemento)">-</button>

              <button href="#" class="btn btn-primary" @click="aumentar(elemento); reduceStock(elemento)" v-if="elemento.stock>0">+</button>
              <button href="#" class="btn btn-primary disabled" @click="aumentar(elemento); reduceStock(elemento)" v-else-if="elemento.stock<=0">+</button>

              <button href="#" class="btn btn-primary" @click="quitar(elemento)">x</button>
          </div>
            </div>
          </div>
        </div>
      </div>

    </div>

    <div class="modal-footer">
      
      <p >Total: ${{totalCart}}</p>
      <button type="button" class="btn btn-primary" @click="vaciarCart()">vaciar carrito</button>
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
    },
    totalCart:{
      type: Number,
      required: true,
    }
  },

  methods:{
    disminuir(elemento){
     this.$emit("click1", elemento )
    },
    aumentar(elemento){
      this.$emit("click2", elemento)
    },
    quitar(elemento){
      this.$emit("click3", elemento)
    },
    vaciarCart(){
      this.$emit("vaciar")
    },
    reduceStock(elemento){
      this.$emit("reduceStock", elemento)
    },
  },
  
}
</script>
