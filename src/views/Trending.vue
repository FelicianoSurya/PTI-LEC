<template>

<div>
  
    <div class="container mt-2 col-md-12 col-sm-9 col-11">
        <div class="pt-4 pb-2 p-0" style="text-align:left">
          <div class="d-flex justify-content-between">
            <h2><b>Top 10 Trending News</b></h2>
            <CountrySelect @changeCountry="changeC($event)" />
          </div>
          <hr class="w-100 mt-2 mb-3">
        </div>
        
        <div v-for="data in news.slice(0, 10)" :key="data.id" class="row mb-3 box-news">
          <div class="col-md-4 p-0 d-flex">
              <img :src="data.urlToImage" alt="image_media">
          </div>  
          <div class="col-md-8 p-3 d-flex flex-column align-items-start justify-content-between information">
            <div class="d-flex flex-column justify-content-between" style="height:100%" >
              <div>
                <h3><b>{{ data.title }}</b></h3>
                <p class="desc">{{ data.description }}</p>
              </div>
              <div class="d-flex justify-content-end">
                <a :href="data.url" target="_blank"><button class="btn btn-secondary btn-sm mb-1">Go To Article</button></a>
              </div>
            </div>
            <div class="card-footer col-12 d-flex justify-content-end text-muted newscard-date">
                <h6>{{ data.publishedAt }}</h6>
            </div> 
          </div>
        </div> 
    </div>

</div>

</template>

<script>
import CountrySelect from '../components/CountrySelect.vue'

export default {
  name: 'Trending',
  components : {
      CountrySelect,
  },
  data(){
    return {
      news : [],
      data : {
        language : 'us',
      }
    }
  },
  mounted(){
    this.getNews();
  },
  methods : {
    getNews(){
      axios.get('https://newsapi.org/v2/top-headlines? &country=' + this.data.language + '&apiKey=6c0c839f2c914a1ea4fbef97585da424').then((res)=>{
        this.news = res.data.articles;
      });
    },
    changeC(country){
      this.data.language = country;
      this.getNews();
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import '../assets/css/news.css';
</style>