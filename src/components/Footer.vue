<template>
  
    <div class="container-fluid p-0 mt-5 footer pt-3 footer-details">
        <div class="col-md-12 d-flex flex-column align-items-center text-center px-5">
            <img src="../assets/images/logo1.png" alt="">
            <p class="footer-desc pt-2"><b>
                World E-News is the world's leading <br>
                space for upadated global news.
            </b></p>
        </div>  
        <div class="text-center footer-note pb-2">
            <i>World E-News by Kelompok Tiny</i>
        </div>
    </div>
   
</template>

<script>
export default {
  name: 'Footer',
  props: {
    title : String,
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import '../assets/css/footer.css';
</style>