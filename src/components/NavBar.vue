<template>

<div class=" sticky-top">
  <nav class="navbar navbar-expand-lg navbar-light bg-light ">
    <div class="container">
      <a class="navbar-brand" href="#">Rick and Morty</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav ms-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <a class="nav-link" href=""><router-link to="/">Home</router-link></a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href=""><router-link to="/login">Logout</router-link></a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</div>

</template>


<script>

</script>


<style>
.bg-light{
  background-color: #b8fb7b !important;
}

.navbar-brand{
  font-weight: bold;
  color: #44281d !important;
}

</style>