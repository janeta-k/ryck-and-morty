<template>
<NavBar />
     <Carrusel />
     <h2 class="text-center mt-5">Personajes Rick and Morty</h2>
     <Products/>
     <Footer />
</template>

<script>
import NavBar from '@/components/NavBar.vue'
import Footer from '@/components/Footer.vue'
import Carrusel from '@/components/Carrusel.vue'
import Products from '@/components/Products.vue'

export default {
  components:{
    Carrusel,
    Products,
    NavBar,
    Footer,
  },
}
</script>
