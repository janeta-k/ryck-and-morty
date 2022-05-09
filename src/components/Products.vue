<template>

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
  <div class="container mb-5">
   
    <div class="row justify-content-center">
      <div
        class="card col-6 col-sm-2 m-3 p-0"
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
          <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#exampleModal" @click="showMore(item)" >
              Ver detalles
          </button>
        </div>

<!--@click="showMore(item.id)"-->

       

      </div>
    </div>

     <!-- Modal -->
<div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true" >
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel" >{{modal.name}}</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
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
  </div>


</template>

<script>

export default {
 

  data() {
    return {
      result: [],
      buscar: "",
      modal:{
        name: "",
        origin: "",
        status:"",
        gender:""
      },
    };
  },
  methods:{
   showMore(object){
     //this.modal.title = object.name
     this.modal = {
       name: object.name,
       origin:object.origin.name,
       status:object.status,
       gender:object.gender,
     }
     console.log(object)
   }
   
 },
  mounted() {
    fetch("https://rickandmortyapi.com/api/character")
      .then(res => res.json())
      .then(todos => (this.result = todos.results));
  },
  computed: {
    items() {
      return this.result.filter(item => {
        return item.name.toLowerCase().includes(this.buscar.toLowerCase());
      });
    },
  }
  };
</script>