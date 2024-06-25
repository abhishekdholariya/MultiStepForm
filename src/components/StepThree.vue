<template>
    <div class="container">
        <div class="content">
                <h2 class="form-group">Work Experiences</h2>
                <div class="form-group">
                    <label for="experience">Experience</label>
                    <input type="text" id="experience" v-model="formData.experience" placeholder="Enter Experience" />
                    <span v-if="validateField && !formData.experience" class="error">Experience is required</span>
                </div>
                <div class="form-group">
                    <label for="position">Position</label>
                    <input type="text" id="position" v-model="formData.position" placeholder="Enter Position" />
                    <span v-if="validateField && !formData.position" class="error">Position is required</span>
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
    name: 'StepThree',
    props: ['formData'],
    data() {
      return {
        validateField:false
      }
    },
    methods: {
        validateAndNextStep() {
          this.validateField = true;
            if (this.validateForm()) {
                this.nextStep();
            }
        },
        validateForm() {
            if (!this.formData.experience || !this.formData.position) {
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
  