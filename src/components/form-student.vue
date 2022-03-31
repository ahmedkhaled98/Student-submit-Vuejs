<template>
    
<div class="container py-5">
  <h2 class="text-center" style="color:#0F52BA;">SUBMISSION</h2>
  <div class="row py-5 mt-3">
    <div class="col-lg-4">

      <img src="@/assets/form.png" alt="" class="w-100">
    </div>
    <div class="col-lg-8 m-auto px-5">
     <form class="">
       <input type="text" placeholder="enter your first-name" v-model="fname" ><br>
       <input type="text" placeholder="enter your last-name" v-model="lname" ><br>
       <input type="email" placeholder="email"  v-model="email"><br>
       <input type="text" placeholder="gender"  v-model="gender"><br>
       <button class="button-63 px-5" @click.prevent="add" @click="showmsg=true">SUBMIT</button>
    </form>
    <div v-if="showmsg" id="myDIV" class="alert alert-success mt-2 ml-5 w-50 text-center" role="alert">
           <p> Submited Successfuly </p>
           </div>
    </div>
  </div>
 
</div>
<footerComp/>
</template>
 
<script>

import axios from 'axios'
    export default {
        name:'formComp',
    data()
    {
        return {
       fname: "",
       lname:"" ,
       email:"",
       gender:"",
       showmsg:false
             } 
    },
      methods:
      {
         add(){
           
            axios.post('http://localhost:3000/students',{
                first_name:this.fname,
                last_name:this.lname,
                email:this.email,
                gender:this.gender
            })
            .then(res=>{
                console.log(res)
            })
            .catch(error=>{
                console.log(error)
            })
         }
      }      

    }
</script>

<style scoped>
 input[type=text], input[type=email]{
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

.button-63 {
  align-items: center;
  background-image: linear-gradient(120deg,#002366, #0F52BA 50%,#f15a25);
  border: 0;
  border-radius: 8px;
  box-shadow: rgba(151, 65, 252, 0.2) 0 15px 30px -5px;
  box-sizing: border-box;
  color: #FFFFFF;
  font-family: Phantomsans, sans-serif;
  font-size: 20px;
  justify-content: center;
  padding: 1%;
  cursor: pointer;
  margin-left: 33%;
}


#myDIV {
 
 margin-left: 20%;
}
</style>
