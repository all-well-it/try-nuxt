<template>
  <div>
    <button @click="makeFirstRequest">Make First Request</button>
    <button @click="makeSecondRequest">Make Second Request</button>
  </div>
</template>

<script>
import axios from 'axios';
axios.defaults.withCredentials = true;

let token;

export default {
  methods: {
    makeFirstRequest() {
      // Configuring Axios to include credentials such as cookies
      axios.post('https://dev.mya-allwell-test.com/otp', {"email": "vasco@rossi.it"})
        .then(response => {
          token = response.data.token
          console.log('First request data:', response.data);
        })
        .catch(error => {
          console.error('Error making the first request:', error);
        });
    },
    makeSecondRequest() {
      // Configuring Axios to include credentials such as cookies
      console.log(token)
      axios.post('https://dev.mya-allwell-test.com/otp/verify', {"token": token, "code": "424242"})
        .then(response => {
          console.log('Second request data:', response.data);
        })
        .catch(error => {
          console.error('Error making the second request:', error);
        });
    }
  }
}
</script>

<style>
/* Add your styles here */
</style>
