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
                <h2>User Photo</h2>
                <div class="form-group">
                    <label for="profile">Select Profile</label>
                    <input type="file" id="profile" @change="handleFileUpload" required />
                </div>
                <div class="button-container">
                    <button type="button" @click="previousStep">Previous</button>
                    <button type="submit" @click="submitForm">Submit</button>
                </div>
        </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'StepThree',
    props: ['formData'],
    methods: {
      handleFileUpload(event) {
        this.formData.profile = event.target.files[0];
      },
      submitForm() {
        this.$emit('submit-form');
      },
      previousStep() {
        this.$emit('previous-step');
      }
    }
  }
  </script>
  