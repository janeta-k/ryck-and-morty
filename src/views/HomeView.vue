<template>
     <Carrusel />
     <h2 class="text-center mt-5">Personajes Rick and Morty</h2>
     <Products/>
</template>

<script>
import Carrusel from '@/components/Carrusel.vue'
import Products from '@/components/Products.vue'

export default {
  components:{
    Carrusel,
    Products
  },
}
</script>
