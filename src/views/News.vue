<template>
  
    <div class="container mt-2 col-md-11 col-sm-9 col-11">
        <div v-for="data in news" :key="data.id" class="row mt-5 box-news">
          <div class="col-md-4 p-0 d-flex">
              <img :src="data.media" alt="image_media">
          </div>  
          <div class="col-md-8 p-3 d-flex flex-column align-items-start justify-content-between information">
            <div>
              <h3><b>{{  }}</b></h3>
              <p class="desc">{{  }}</p>
            </div>
            <div class="card-footer col-12 d-flex justify-content-end text-muted">
                <h6>{{  }}</h6>
            </div> 
          </div>
        </div> 
    </div>

</template>

<script>
export default {
  name: 'News',
  props: {
   
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import '../assets/css/news.css';
</style>