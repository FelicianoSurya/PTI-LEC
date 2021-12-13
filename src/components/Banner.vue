
<template>
  
  <div>
  
    <div class="container-fluid p-0">
        <div class="background d-flex flex-column justify-content-center align-items-center">
          <img src="../assets/images/logo2.png" alt="">
        </div> 
    </div>

  </div>

</template>

<script>
export default {
  name: 'Banner',
  props: {
    title : String,
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import '../assets/css/news.css';
</style>
