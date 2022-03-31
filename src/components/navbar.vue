<template>
<nav class="navbar navbar-light navbar-expand-md bg-faded justify-content-center" style="background-color:#0F52BA; color:white;">
    <div class="container">
        <a class="navbar-brand d-flex w-50 m-auto" style="color:white;" aria-current="page" to="/home">
         <img src="@/assets/logo.png" alt="" width="50" height="50" class="d-inline-block align-text-top">
        </a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#collapsingNavbar3">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="navbar-collapse collapse w-100" id="collapsingNavbar3">
            <ul class="navbar-nav w-50 justify-content-center">
                <li class="nav-item">
                    <router-link class="nav-link" style="color:white;" aria-current="page" to="/home">HOME</router-link>
                </li>
                <li class="nav-item">
                   <router-link class="nav-link" style=" color:white;" to="/register">FORM</router-link>
                </li>
                <li class="nav-item">
                     <router-link class="nav-link" style=" color:white; " to="/students">STUDENTS</router-link>
                </li>
            </ul>
            
        </div>
    </div>
</nav>
</template>

<script>
    export default {
        name:'navbarComp',
         data(){
          return{
             isActive:false
          }
        },
  methods(){
    
    
  }

    }
</script>

<style scoped>
.active{
  border-bottom: solid 2px #f15a25;
}

</style>