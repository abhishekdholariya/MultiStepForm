<template>
  <div class="container">
    <div class="content">
      <h2 class="form-group">Personal Information</h2>
      <div class="form-group">
        <label for="fname">First Name:</label>
        <input type="text" v-model="formData.fname" id="fname" placeholder="Enter FirstName" />
        <span v-if="validateField && !formData.fname" class="error">First Name is required</span>
      </div>
      <div class="form-group">
        <label for="lname">Last Name:</label>
        <input type="text" v-model="formData.lname" id="lname" placeholder="Enter LastName" />
        <span v-if="validateField && !formData.lname" class="error">Last Name is required</span>
      </div>
      <div class="form-group">
        <label for="bod">Date of Birth:</label>
        <input type="date" v-model="formData.bod" id="bod" />
        <span v-if="validateField && !formData.bod" class="error">Date of Birth is required</span>
      </div>
      <div class="form-group">
        <label for="phonenumber">Phone Number:</label>
        <input type="tel" v-model="formData.phonenumber" id="phonenumber" placeholder="Enter PhoneNumber" />
        <span v-if="validateField && !formData.phonenumber" class="error">Phone Number is required</span>
      </div>
      <div class="form-group">
        <label for="email">Email:</label>
        <input type="email" v-model="formData.email" id="email" placeholder="Enter Email" />
        <span v-if="validateField && !formData.email" class="error">Email is required</span>
        <span v-if="validateField && formData.email && !isValidEmail(formData.email)" class="error">Invalid email format</span>
      </div>
      <div class="button-container">
        <button class="button" @click="validateAndNextStep" type="button">Next</button>
      </div>
    </div>
  </div>
</template>
  
<script>
  export default {
    name: 'StepOne',
    props: ['formData'],
    data() {
      return {
        validateField: false
      }
    },
    methods: {
      validateAndNextStep() {
        this.validateField = true;
        if (this.validateForm()) {
          this.$emit('next-step');
        }
      },
      validateForm() {
        return this.formData.fname && this.formData.lname && this.formData.bod && this.formData.phonenumber && this.formData.email && this.isValidEmail(this.formData.email);
      },
      isValidEmail(email) {
        const emailPattern = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
        return emailPattern.test(email);
      }
    }
  }
</script>
  