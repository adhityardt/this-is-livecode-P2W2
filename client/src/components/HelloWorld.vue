<template>
  <div >
    <h1>this is kura</h1>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data (){
    return {

    }
  },
  methods: {
    getImage: function () {
      axios.get('http://35.197.135.159/image', {
        headers: {
          authorization: localStorage.getItem('authorization')
        }
      })
      .then(response => {
        this.listPhoto = response.data.result
      })
      .catch(err => {
        this.error = err
      })
    }
  }
}
</script>

<style >
</style>
