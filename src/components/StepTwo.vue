<template>
    <div class="container">
        <div class="content">
            <h2 class="form-group">Education</h2>
            <div class="form-group">
                <label for="degree">Degree</label>
                <input type="text" id="degree" v-model="formData.degree" placeholder="Enter Degree Name" />
                <span v-if="validateField && !formData.degree" class="error">Degree is required</span>
            </div>
            <div class="form-group">
                <label for="school">School/College</label>
                <input type="text" id="school" v-model="formData.school" placeholder="Enter College Name" />
                <span v-if="validateField && !formData.school" class="error">School is required</span>
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
    data() {
        return {
            validateField: false,
        };
    },
    methods: {
        validateAndNextStep() {
            this.validateField = true;
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
