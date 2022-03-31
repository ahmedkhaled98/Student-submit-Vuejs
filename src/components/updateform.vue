<template>
    <div class="container py-5">
        <h2 class="text-center" style="color:#0F52BA;">UPDATE INFO</h2>
  <div class="row py-5 mt-3">
    <div class="col-lg-4 py-5 ">

      <img src="@/assets/flame-1209.png" alt="" class="w-100">
    </div>
    <div class="col-lg-8 m-auto py-5 px-5">
     <form>
       <input type="text" placeholder="enter your first-name"  v-model="fname"><br>
       <input type="text" placeholder="enter your last-name" v-model="lname" ><br>
       <input type="email" placeholder="email"  v-model="email"><br>
       <input type="text" placeholder="gender"  v-model="gender"><br>
         <button class="button-63 px-5" @click.prevent="updateinfo ,showmsg=true"  >UPDATE</button>
      </form>
      <div v-if="showmsg" id="myDIV" class="alert alert-success mt-2 ml-5 w-50 text-center" role="alert">
           <p> Student updated successfuly </p>
           </div>
    </div>
  </div>
 
</div>
<footerComp/>
</template>

<script>

   import axios from 'axios'
    export default {
        name:'updateComp',
    data(){
        return{
     id:'',
     fname:'',
     lname:'',
     email:'',
     gender:'',
     showmsg:false,
        }
    },
      created(){
             
             
             this.getbyid()
             console.log(this.fname)
            },
        methods:{
        //    msg(){
        //        var x = document.getElementById("myDIV");
        //     if (x.style.display === "none") {
        //            x.style.display = "block";
        //         } else {
        //                x.style.display = "none";
        //           }
        //    },
        updateinfo(){
            
            const updateduser={}
            if(this.fname){
                updateduser.first_name=this.fname;
            }
            if(this.lname){
                updateduser.last_name=this.lname;
            }
            if(this.email){
                updateduser.email=this.email;
            }
            if(this.gender){
                updateduser.gender=this.gender;
            }
            this.id=this.$route.params.id
        axios.patch(`http://localhost:3000/students/${this.id}`, updateduser
         )
         
     
    },
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
