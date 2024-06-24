<template>
    <div>
      <component :is="currentStepComponent" :formData="formData" 
                 @next-step="nextStep" @previous-step="previousStep" 
                 @submit-form="submitForm"></component>
    </div>
  </template>
  
  <script>
  import StepOne from './StepOne.vue';
  import StepTwo from './StepTwo.vue';
  import StepThree from './StepThree.vue';
  import StepFour from './StepFour.vue';

  export default {
    name: 'MultiStepForm',
    components: {
      StepOne,
      StepTwo,
      StepThree,
      StepFour
    },
    data() {
      return {
        currentStep: 1,
        formData: {
          fname: '',
          lname: '',
          bod:'',
          phonenumber:'',
          email: '',
          degree:'',
          school:'',
          experience:'',
          position:'',
          profile:''
        }
      }
    },
    computed: {
      currentStepComponent() {
        switch (this.currentStep) {
          case 1:
            return StepOne;
          case 2:
            return StepTwo;
          case 3:
            return StepThree;
          case 4:
            return StepFour;
          default:
            return StepOne;
        }
      }
    },
    methods: {
      nextStep() {
        if (this.currentStep < 4) {
          this.currentStep++;
        }
      },
      previousStep() {
        if (this.currentStep > 1) {
          this.currentStep--;
        }
      },
      submitForm() {
        console.log('Form submitted:', this.formData);
        alert('Form submitted!');
        // Reset form
        this.currentStep = 1;
        this.formData = {
          fname: '',
          lname: '',
          bod:'',
          phonenumber:'',
          email: '',
          degree:'',
          school:'',
          experience:'',
          position:'',
          profile:''
        };
      }
    }
  }
  </script>