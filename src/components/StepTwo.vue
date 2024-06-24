<template>
    <div class="container">
        <div class="content">
                <h2>Education</h2>
                <div class="form-group">
                    <label for="degree">Degree</label>
                    <input type="text" id="degree" v-model="formData.degree" required />
                    <span v-if="!formData.degree" class="error">Degree is required</span>
                </div>
                <div class="form-group">
                    <label for="school">School/College</label>
                    <input type="text" id="school" v-model="formData.school" required />
                    <span v-if="!formData.school" class="error">School is required</span>
                </div>
                <div class="button-container">
                    <button class="button" type="button" @click="previousStep">Prev</button>
                    <button class="button" @click="validateAndNextStep" type="submit">Next</button>
                </div>
        </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'StepTwo',
    props: ['formData'],
    methods: {
        validateAndNextStep() {
            if (this.validateForm()) {
                this.nextStep();
            }
        },
        validateForm() {
            if (!this.formData.degree || !this.formData.school) {
                return false;
            }
            return true;
        },
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