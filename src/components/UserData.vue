<template>
  <div>
    <h2>User Data</h2>
    <ul style="list-style: none;">
      <li><strong>First Name:</strong> {{ formData.fname }}</li>
      <li><strong>Last Name:</strong> {{ formData.lname }}</li>
      <li><strong>Date of Birth:</strong> {{ formData.bod }}</li>
      <li><strong>Phone Number:</strong> {{ formData.phonenumber }}</li>
      <li><strong>Email:</strong> {{ formData.email }}</li>
      <li><strong>Degree:</strong> {{ formData.degree }}</li>
      <li><strong>School:</strong> {{ formData.school }}</li>
      <li><strong>Experience:</strong> {{ formData.experience }}</li>
      <li><strong>Position:</strong> {{ formData.position }}</li>
      <li v-if="formData.profile">
        <strong>Profile Image:</strong><br />
        <img :src="profileImage" alt="Profile Image" style="max-width: 200px; max-height: 200px;" />
      </li>
    </ul>
    <button @click="refreshForm">Submit Form</button>
  </div>
</template>

<script>
  export default {
    name: 'UserData',
    props: ['formData'],
    computed: {
      profileImage() {
        return URL.createObjectURL(this.formData.profile);
      }
    },
    methods: {
      refreshForm() {
        this.$emit('refresh-form');
      }
    }
  }
</script>
