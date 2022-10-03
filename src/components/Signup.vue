<template>
  <h1>Web Form</h1>
  <form @submit.prevent="handleSubmit">
    <label for="email">Email</label>
    <input type="email" v-model="email" />
    <br />
    <label for="password">Password</label>
    <input type="password" v-model="password" />
    <select v-model="gender">
      <option value="male">male</option>
      <option value="Female">Female</option>
    </select>
    <label>Select fav ICecrema</label><br>   
    <input type="checkbox" value="chocolate"  v-model="icecrweam"><label>chocolate</label>
    <input type="checkbox" value="vannila" v-model="icecrweam"><label>vannila</label>
    <input type="checkbox" value="mocha" v-model="icecrweam"><label>mocha</label>
    <br />
    <label>Skills</label>
    <input type="text" v-model="tempSkill" @keyup.enter="addSkill"/>
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="deleteSkill(skill)">{{skill}}</span>
    </div>
    <button class="submit">submit</button>

  </form>
  <p>email :{{ email }}</p>
  <p>password :{{ password }}</p>
  <p>gender : {{ gender }}</p>
   <p>Icecrema : {{icecrweam}}</p>
   <p>skills: {{ skills }}</p>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      gender: "Female",
      icecrweam : [],
      skills : [],
      tempSkill :""

    };
  },
  methods:{
    addSkill(e){
      if(!this.skills.includes(this.tempSkill) && this.tempSkill ){
        this.skills.push(this.tempSkill)
      }      
      this.tempSkill = '';
      
    },
    deleteSkill(skill){
      this.skills = this.skills.filter((item) => 
          {  return skill!==item } 
        )
    } ,
    handleSubmit(){
      console.log("All values submited successfully")
    }
    
  }
};
</script>

<style>
form {
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}
input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}
.pill {
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
button {
  background: #0b6dff;
  border: 0;
  padding: 10px 20px;
  margin-top: 20px;
  color: white;
  border-radius: 20px;
}
.submit {
  text-align: center;
}
.error {
  color: #ff0062;
  margin-top: 10px;
  font-size: 0.8em;
  font-weight: bold;
}
</style>