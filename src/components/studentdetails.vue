<template>
    
 
  <div class="container py-5">
  <div class="row py-5">
    <div class="col-lg-6">
      <img src="@/assets/s3.jpg" alt="" class="w-75">
    </div>
    <div class="col-lg-6 m-auto">
     <p style="color:#0F52BA; font-size:30px" class="text-left"><span style="color:#f15a25">Name:</span>{{fname}}{{lname}}</p>
     <p style="color:#0F52BA; font-size:30px" class="text-left"><span style="color:#f15a25">Gender:</span>{{gender}}</p>
     <p style="color:#0F52BA; font-size:30px" class="text-left"><span style="color:#f15a25">Email:</span>{{email}}</p>
     <router-link class="button-63 px-5" :to="`/students/studentdetails/${id}`">update</router-link>
    </div>
  </div>
 
</div>
    
 
 
<footerComp/>
</template>

<script>
      import axios from 'axios'
    export default {
        name:'detailsComp',
        
        data(){
     return {
     id:'',
     fname:'',
     lname:'',
     gender:'',
     email:''
     }},
     created(){
       this.getbyid()
     },
     methods:{

     getbyid(){
     this.id=this.$route.params.id
     axios.get(`http://localhost:3000/students?id=${this.id}`).
     then(res=>{
        console.log(res.data)
        for (let i = 0; i < res.data.length; i++) {
             this.fname=res.data[i].first_name
             this.lname = res.data[i].last_name
             this.email =res.data[i].email
             this.gender =res.data[i].gender
          } 
          } )
        .catch(error=>{
            console.log(error)
        })
     },
     
     
    


     }  
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

    