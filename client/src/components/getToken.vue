<template>
 <div>
  <form>
    <h3>Get Token</h3>
    <div class="form-group">
      <label for="exampleInputEmail1">Email address</label>
      <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email">
      <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
    </div>
    <div class="form-group">
      <label for="exampleInputPassword1">Full Name</label>
      <input type="password" class="form-control" id="exampleInputPassword1" placeholder="Password">
    </div>
    <button type="submit" class="btn btn-primary">Submit</button>
  </form>
 </div>
</template>

<script>
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
          axios.post('http://35.198.212.156/request-token', {
            email: this.email,
            name: this.name
          })
          .then(response => {
            if (response.data.uid) {
              this.success = 'Add token sucess'
              localStorage.setItem('authorization', response.data.uid)
            }
          })
          .catch(err => {
            this.error = err
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
