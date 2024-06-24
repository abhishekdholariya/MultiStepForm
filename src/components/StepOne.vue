<template>
    <div class="container">
        <div class="content">
                <h2 class="form-group">Personal Information</h2>
                <div class="form-group">
                    <label for="fname">Frist Name:</label>
                    <input type="text" v-model="formData.fname" id="fname" required />
                    <span v-if="!formData.fname" class="error">First Name is required</span>
                </div>
                <div class="form-group">
                    <label for="lname">Last Name:</label>
                    <input type="text" v-model="formData.lname" id="lname" required />
                    <span v-if="!formData.lname" class="error">Last Name is required</span>
                </div>
                <div class="form-group">
                    <label for="bod">Date of Birth:</label>
                    <input type="text" v-model="formData.bod" id="bod" required />
                    <span v-if="!formData.bod" class="error">Date of Birth is required</span>
                </div>
                <div class="form-group">
                    <label for="phoneumber">Phone Number:</label>
                    <input type="number" v-model="formData.phonenumber" id="phonenumber" required />
                    <span v-if="!formData.phonenumber" class="error">Phone Number is required</span>
                </div>
                <div class="form-group">
                    <label for="email">Email</label>
                    <input type="email" v-model="formData.email" id="email" required />
                    <span v-if="!formData.email" class="error">Email is required</span>
                </div>
                <div class="button-container">
                    <button class="button" @click="validateAndNextStep" type="submit">Next</button>
                </div>
        </div>
    </div>
</template>
  
  <script>
  export default {
    name: 'StepOne',
    props: ['formData'],
    methods: {
        validateAndNextStep() {
            if (this.validateForm()) {
                this.nextStep();
            }
        },
        validateForm() {
            if (!this.formData.fname || !this.formData.lname || !this.formData.bod || !this.formData.phonenumber || !this.formData.email) {
                return false;
            }
            return true;
        },
        nextStep() {
            this.$emit('next-step');
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
.error{
    color: rgb(230, 35, 35);
}
</style>
  