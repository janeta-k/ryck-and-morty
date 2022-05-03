<template>
    <footer id="contacto" class="piedepagina container-fluid ">
  <div>
    <div class="row d-flex">


      <div class="pb-4 col-xs-12 col-sm-4">
        <div class="ubi">
          <h4>Encuéntranos en:</h4>
          <a href=""><i class="fa-solid fa-location-dot"></i>
            Mall Marina Arauco (1er Nivel) | Av. Libertad 1348 Modulo A-73 , Viña del Mar, Valparaíso, Chile</a>
        </div>
      </div>

      <div class="pb-4 col-xs-12 col-sm-4">
        <h4 class="comparte">Comparte</h4>
        <div class="redes-sociales">
          <a href=""><i class="fa-brands fa-instagram"></i></a>
          <a href=""><i class="fa-brands fa-facebook"></i></a>
          <a href=""><i class="fa-brands fa-twitter"></i></a>
        </div>
      </div>

      <div class="pb-4 col-xs-12 col-sm-4">
        <div class="contacto">
          <h4>Contáctanos</h4>
          <a href=""><i class="fa-brands fa-whatsapp"></i> +56 9 1234567</a> <br>
          <a href=""><i class="fa-solid fa-envelope"></i>contacto@rickandmorty.com</a>
        </div>
      </div>

      <div class="pt-3 pb-3 col-12 copy">
        <h4>Copyright &copy; 2022 - Página creada por  Nicole Arriagada | Janet
          Santi | Elizabett Fernández | Guillermo Berna - Todos los derechos reservados</h4>
      </div>

    </div>
  </div>
</footer>
</template>

<script>
</script>

<style>
.piedepagina {
  background-color: #97ce4c;
  padding-top: 30px;
}

/*sección contáctanos */
.contacto {
  display: flex;
  flex-direction: column;
  text-align: center;
}

.contacto h4 {
  margin: 0 35px;
  margin-bottom: 15px;
  font-weight: bold;
  color: 	#44281d	;
}

.contacto a {
  color: white;
}

.contacto a:hover{
  color: #c8a155;
}

/*sección redes sociales */
.comparte {
  text-align: center;
  font-weight: bold;
  color: 	#44281d	;
}

.redes-sociales{
  display: flex;
  justify-content:space-around;
  margin: 0 126px;
  margin-top: 17px;
  margin-bottom: 10px;
}

.redes-sociales a {
  font-size: 15px;
  color: white;
}

.redes-sociales a:hover{
  color: #c8a155;
}


/*sección de la ubicación */
.ubi {
  text-align: center;    
}

.ubi h4 {
  font-weight: bold;
  color: 	#44281d	;
}

.ubi a {
  color: white;
}

.ubi a:hover{
  color: #c8a155;
}


/*sección copyright */
.copy {
  background-color: 	#44281d	; 
}

.copy h4 {
  color: white;
  text-align: center;
  font-size: 12px;
  margin-top: 5px;
}

</style>
