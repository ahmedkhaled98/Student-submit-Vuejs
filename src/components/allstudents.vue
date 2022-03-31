<template>
    <div class="container py-5">
  <div class="row py-5">
    <div class="col m-auto py-5">
<table class="table table-info table-striped">
          <thead>
            <tr>
              <th scope="col">ID</th>
              <th scope="col">Name</th>
              <th scope="col">Email</th>
              <th scope="col">Gender</th>
               
            </tr>
          </thead>
          <tbody>
            <tr v-for="student in students" :key="student.id">
              <th scope="row">{{ student.id }}</th>
              <th scope="row">{{ student.first_name}} {{ student.last_name}}</th>
              <th scope="row">{{ student.email}}</th>
              <th scope="row">{{ student.gender}}</th>
              <td>
                  <router-link class="btn btn-primary" :to="`/students/${student.id}`">See More</router-link>
              </td>
              <td> <button class="btn btn-danger" @click="Delete(student)"> Delete</button></td>
            </tr>
          </tbody>
 </table>
 <button @click=" Deleteall()" class="btn btn-danger px-5 mt-2" > Delete All</button>
     
    </div>
    
  </div>
 
</div>
<footerComp/>
</template>

<script>
import axios from 'axios'
    export default {
        name:'studentsComp',
        data(){
        return {
          students:[]
       
            } },
        created(){
                this.getstudents()
            },
    
            // updated(){
            //       this.getstudents()
            // },
      methods:{
         getstudents(){
            axios.get('http://localhost:3000/students')
            .then(res=>{
               this.students=res.data
              
            })
            .catch(error=>{
                console.log(error)
            })
         },
       async Delete(studentt){
          console.log(studentt)
       await axios.delete(`http://localhost:3000/students/${studentt.id}`)
       .then(res=> {
       this.students.splice(studentt.id, 1);
       this.getstudents()  
        console.log(res) 
         })},
        async Deleteall(){
          console.log("done")
          for(let i=0;i<this.students.length-5;i++){
       await axios.delete(`http://localhost:3000/students/${this.students[i].id}`)
       .then(res=> {
       this.students.splice(this.students[i].id,1); 
        console.log(res)  
        })    }      },

   }
    } 
</script>

<style scoped>

</style>

   