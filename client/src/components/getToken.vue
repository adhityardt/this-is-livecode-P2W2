<template>
 <div>
  <form>
    <h3>Get Token</h3>
    <div class="form-group">
      <label for="exampleInputEmail1">Email address</label>
      <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email" v-model="email">
      <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
    </div>
    <div class="form-group">
      <label for="exampleInputPassword1">Full Name</label>
      <input type="text" class="form-control" id="exampleInputPassword1" placeholder="Enter your full name" v-model="name">
    </div>
    <button type="submit" class="btn btn-primary" @click="addToken">Get Token</button>
  </form>
 </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'getToken',
  data () {
    return {
      email: '',
      name: ''
    }
  },
  methods: {
    addToken: function () {
      axios.post('http://35.197.135.159/request-token', {
        email: this.email,
        name: this.name
      })
      .then(response => {
        // console.log(response)
        if (response.data.uuid) {
          console.log('Add token sucess')
          console.log('This is your token/uuid', response.data.uuid)
          localStorage.setItem('authorization', response.data.uuid)
        }
      })
      .catch(err => {
        console.log(err)
      })
    }
  }
}
</script>

<style>
form
{
  border:thin black solid;
  margin:20px;
  padding:20px;
}
</style>
