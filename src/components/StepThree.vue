<template>
    <!-- <div>
      <h2>Step 3</h2>
      <form @submit.prevent="submitForm">
        <label for="password">Password:</label>
        <input type="password" v-model="formData.password" id="password" required />
        <button type="button" @click="previousStep">Previous</button>
        <button type="submit">Submit</button>
      </form>
    </div> -->
    <div class="container">
        <div class="content">
                <h2>Work Experiences</h2>
                <div class="form-group">
                    <label for="experience">Experience 1</label>
                    <input type="text" id="experience" v-model="formData.experience" required />
                </div>
                <div class="form-group">
                    <label for="position">Position</label>
                    <input type="text" id="position" v-model="formData.position" required />
                </div>
                <div class="button-container">
                    <button class="button" type="button" @click="previousStep">Prev</button>
                    <button class="button" @click="nextStep" type="submit">Next</button>
                </div>
        </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'StepThree',
    props: ['formData'],
    methods: {
      nextStep() {
        this.$emit('next-step');
      },
      previousStep() {
        this.$emit('previous-step');
      }
    }
  }
  </script>

  <style scoped>
.container {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
}
.content {
    padding: 20px;
    background: #f8f9fa;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}
.form-group {
    color: black;
}
.button-container {
    text-align: right;
}
</style>
  