<template>
  <div class="container">
    <form class="card" @submit.prevent="submitHandler">
      <h1>Your profile</h1>
      <div class="row">
        <div class="form-element mr-2">
          <label for="name">Your name</label>
          <input type="text" id="name" placeholder="Введи имя" v-model.trim="name">
          <span v-if="errors.name"><small>{{ errors.name }}</small></span>
        </div>

        <div class="form-element mr-2">
          <label for="age">Your Age</label>
          <input type="number" id="age" v-model.number="age">
        </div>

        <div class="form-element">
          <label for="city">Profession</label>
          <select id="city" v-model="job">
            <option value="programmer">Programmer</option>
            <option value="teacher">Teacher</option>
            <option value="drummer">Drummer</option>
            <option selected value="driver">Driver</option>
          </select>
        </div>
      </div>


      <div class="checkbox-container">
        <span class="label">Are you married?</span>
        <div class="checkbox">
          <label><input type="radio" name="married" value="true" v-model="isMarried" /> Yes</label>
        </div>

        <div class="checkbox">
          <label><input type="radio" name="married" value="false" v-model="isMarried" /> No</label>
        </div>
      </div>

      <div class="checkbox-container">
        <span class="label">Choose your hobbies</span>
        <div class="checkbox">
          <label><input type="checkbox" value="reading" v-model="hobbie"/>Reading</label>
        </div>
        <div class="checkbox">
          <label><input type="checkbox" value="cycling" v-model="hobbie" />Cycling</label>
        </div>
        <div class="checkbox">
          <label><input type="checkbox" value="walking" v-model="hobbie" />Walking</label>
        </div>
        <div class="checkbox">
          <label><input type="checkbox" value="swiming" v-model="hobbie" />Swimming</label>
        </div>
      </div>

      <button type="submit" class="btn primary">Submit</button>
    </form>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        name: '',
        age: 20,
        job: "programmer",
        isMarried: "false",
        hobbie: [],
        errors: {
          name: ""
        }
      }
    },
    methods: {
      submitHandler() {
        if(this.isValidated())
        {
           console.log(this.name)
        } 
        
        console.log(this.age)
        console.log(this.isMarried)
        console.log(this.hobbie)
      },
      isValidated() {
        if(!this.name)
        {
          this.errors.name = "Name should not be empty!"
        }
        else {
          this.errors.name = ""
        }  
        return !!this.name

      }
    }
  }
</script>

<style>

</style>
