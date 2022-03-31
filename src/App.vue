<template>
 
  <navbarComp/>
  
  <router-view></router-view>
  
  <footerComp/>

</template>

<script>

import navbarComp from './components/navbar.vue'
import footerComp from './components/footer.vue'

// import detailsComp from './components/studentdetails.vue'
// import  formComp from './components/form-student.vue'
// import  studentsComp from './components/allstudents.vue'

export default {
  name: 'App',
  components: {
     navbarComp,
     footerComp,
     
  }
}
</script>

<style>

</style>
