<template>
  <form @submit.prevent="submit">
    <label for="">email</label>
    <input type="email" required v-model="email">
    <label for="">password</label>
    <input type="password" required v-model="password">
    <div v-if="passworderror" class="error">{{ passworderror }}</div>
    <label for="">role</label>
    <select name="" id="" v-model="role">
      <option value="developer">web developer</option>
      <option value="designer">web designer</option>
    </select>
    <div class="terms">
      <input type="checkbox" v-model="terms" required>
      <label for="">Accept terms and condition</label>
    </div>
    <div>
      <input type="checkbox" value="first" v-model="names">
      <label for="">first</label>
    </div>
    <div>
      <input type="checkbox" value="second" v-model="names">
      <label for="">second</label>
    </div>
   <label for="">Skills:</label>
  <input type="text" v-model="tempSkill" @keyup.alt="addskill">
  <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="delete(skills)">{{ skill }}</span>
    </div>
    <div class="submit">
      <button>create an account</button>
    </div>
  </form>  
  <p>email:{{ email }}</p>
    <p>password:{{ password }}</p>
    <p>role:{{ role }}</p>
    <p>terms:{{ terms }}</p>
    <p>names:{{ names }}</p>
</template>

<script>
export default {
data(){
   return{
      email:'',
      password:'',
      role:'',
      terms:'',
      names:[],
      tempSkill:'',
      skills:[],
      passworderror:''
   }
},
methods:{
   addskill(e){
      if(e.key === ',' && this.tempSkill){
         if(!this.skills.includes(this.tempSkill)){
         this.skills.push(this.tempSkill)
         }
         this.tempSkill=''
      }
   },
   delete(skill){
         this.skills=this.skills.filter((item)=>{
            return skill !== item
         })
   },
   submit(){
      //validate password
      this.passworderror=this.password.length > 5 ?
      '' : 'password at least 6 chars'
      if(!this.passworderror){
         console.log('email:',this.email)
         console.log('password:',this.password)
         console.log('role:',this.role)
         console.log('skills:',this.skills)
         console.log('terms:',this.terms)


      }

   }
}
}
</script>

<style>
 form{
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius:10px;
 }
 label{
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight:bold ;
 }
 input, select{
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
 }
 input[type="checkbox"]{
   display: inline-block;
   width: 16px;
   margin: 0 10px 0 0;
   position: relative;
   top: 2px;
 }
 .pill{
   display: inline-block;
   margin: 20px 10px 0 0;
   padding: 6px 12px;
   background: #eee;
   border-radius: 20px;
   font-size: 12px;
   letter-spacing: 1px;
   font-weight: bold;
   color: #777;
   cursor: pointer;
 }
 button{
   background: #0b6dff;
   border: 0;
   padding: 10px 20px;
   margin-top:20px;
   color: white;
   border-radius:20px;
   cursor: pointer;
 }
 .submit{
   text-align: center;
 }
 .error{
   color: #ff0062;
   margin-top: 10px;
   font-size: 0.8em;
   font-weight: bold;
 }
</style>