<template>
  <div class="container">
    <div class="progress-bar">
      <div :class="{'active': currentStep === 1, 'clickable': currentStep > 1}" @click="goToStep(1)">Personal Information</div>
      <div :class="{'active': currentStep === 2, 'clickable': currentStep > 2}" @click="goToStep(2)">Education</div>
      <div :class="{'active': currentStep === 3, 'clickable': currentStep > 3}" @click="goToStep(3)">Work Experiences</div>
      <div :class="{'active': currentStep === 4, 'clickable': currentStep > 4}" @click="goToStep(4)">Select Profile</div>
      </div>
    <component :is="currentStepComponent" :formData="formData" 
        @next-step="nextStep" @previous-step="previousStep" 
        @submit-form="submitForm" @refresh-form="refreshForm"></component>
  </div>
</template>
  
<script>  
  import StepOne from './StepOne.vue';
  import StepTwo from './StepTwo.vue';
  import StepThree from './StepThree.vue';
  import StepFour from './StepFour.vue';
  import UserData from './UserData.vue';
  
  export default {
    name: 'MultiStepForm',
    components: {
      StepOne,
      StepTwo,
      StepThree,
      StepFour,
      UserData
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
          case 5:
            return UserData;
          default:
            return StepOne;
        }
      }
    },
    methods: {
      nextStep() {
        if (this.currentStep < 5) {
          this.currentStep++;
        }
      },
      previousStep() {
        if (this.currentStep > 1) {
          this.currentStep--;
        }
      },
      goToStep(step) {
        if (step <= this.currentStep) {
          this.currentStep = step;
        }
      },
      submitForm() {
        console.log('Form submitted:', this.formData);
        this.currentStep = 5;
      },
      refreshForm() {
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
  
<style>
  .container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  padding: 20px;
  box-sizing: border-box;
  }

  .content {
  max-width: 600px;
  width: 100%;
  padding: 20px;
  background: #f8f9fa;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }

  .form-group {
  margin-bottom: 15px;
  }

  .form-group label {
  display: block;
  margin-bottom: 5px;
  color: #333;
  }

  .form-group input {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  }

  .button-container {
  text-align: right;
  }

  .button {
  padding: 10px 20px;
  color: #fff;
  background-color: #007bff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  }

  .button:hover {
  background-color: #0056b3;
  }

  .error {
  color: #e62323;
  font-size: 0.9em;
  }
  
  .progress-bar {
      display: flex;
      margin-bottom: 20px;
      width: 100%;
      max-width: 600px;
  }
  
  .progress-bar div {
      flex: 1;
      padding: 10px;
      text-align: center;
      cursor: not-allowed;
      border: 1px solid #ccc;
  }
  
  .progress-bar div.active {
      background-color: lightblue;
      cursor: pointer;
  }
  
  .progress-bar div.clickable:hover {
      background-color: lightgreen;
      cursor: pointer;
  }
</style>
  