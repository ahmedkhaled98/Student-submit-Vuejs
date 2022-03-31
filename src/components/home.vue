<template>
    <div>
 <div class="container">
  <div class="row p-0 m-0">
    <div class="col-lg-6">
      <img src="@/assets/stil.png" alt="" class="w-100">
    </div>
    <div class="col-lg-6 m-auto">
     <h1 style="color:#0F52BA; font-size:50px" class="text-left"> WELCOME <br>TO OUR SCHOOL</h1>
     <p style="color:#f15a25; font-size:30px" class="text-left">Want to apply !!</p>
     <router-link class="button-63 px-5" :to="`/register`">APPLY NOW</router-link>
    </div>
  </div>
 
</div>
    </div>
    <footerComp/>
</template>

<script>
    export default {
        name:'homeComp'
    }
</script>

<style scoped>
.button-63 {
  align-items: center;
  background-image: linear-gradient(120deg,#002366, #0F52BA 50%,#f15a25);
  border: 0;
  border-radius: 8px;
  box-shadow: rgba(151, 65, 252, 0.2) 0 15px 30px -5px;
  box-sizing: border-box;
  color: #FFFFFF;
  font-size: 20px;
  justify-content: center;
  padding: 1%;
  cursor: pointer;
  text-decoration: none;
}
</style>