<template>
  <div>
    <form>
      <h3>Post an Image</h3>
      <div class="form-group">
        <label for="exampleInputEmail1">Select an image</label>
        <input type="file" class="form-control" id="exampleInputEmail1" @change="uploadHandler">
        <small id="emailHelp" class="form-text text-muted">Please post an appropriate image</small>
      </div>
      <button type="submit" class="btn btn-primary" @click="uploadImage">POST</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'postImage',
  data () {
    return {
      image: ''
    }
  },
  methods: {
    uploadImage: function () {
      let formData = new FormData()
      formData.append('file', this.image)
      axios.post('http://35.197.135.159/image', formData, {
        'Content-Type': 'multipart/form-data',
        headers: {
          authorization: localStorage.getItem('authorization')
        }
      })
      .then(response => {
        console.log('upload image sucess')
      })
      .catch(err => {
        console.log(err)
      })
    },
    uploadHandler: function (event) {
      this.image = event.target.files[0]
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
