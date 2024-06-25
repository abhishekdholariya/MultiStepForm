<template>
    <div class="container">
        <div class="content">
                <h2>User Photo</h2>
                <div class="form-group">
                    <label for="profile">Select Profile</label>
                    <input type="file" id="profile" @change="handleFileUpload" required />
                    <span v-if="validateField && !formData.profile" class="error">Profile is required</span>
                </div>
                <div class="button-container">
                    <button type="button" @click="previousStep">Previous</button>
                    <button type="submit" @click="validateAndNextStep">Preview Form</button>
                </div>
        </div>
    </div>
</template>
  
<script>
  export default {
    name: 'StepThree',
    data() {
        return {
            validateField:false
        }
    },
    props: ['formData'],
    methods: {
        validateAndNextStep() {
            this.validateField=true;
            if (this.validateForm()) {
                this.submitForm();
            }
        },
        validateForm() {
            if (!this.formData.profile) {
                return false;
            }
            return true;
        },
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
  
