<template>

<div>
      <div class="container mt-2 col-md-11 col-sm-9 col-12 pt-4 top-news">
        <h2><b>News</b></h2>
            <ul class="d-flex sort-news">
              <li class="sort-news col-lg-4 col-md-4 col-sm-4 col-4"><SelectLanguage @changeLanguage="changeC($event)" /></li>
              <li class="sort-news col-lg-4 col-md-4 col-sm-4 col-4"><SortBy @changeSortBy="changeSortBy($event)" /></li> 
              <li class="sort-news col-lg-4 col-md-4 col-sm-4 col-4">
                <Search @changeq="changeq($event)" />
              </li>
            </ul>
      </div>
    
    <div class="container col-md-11 col-sm-9 col-11">
      <hr class="w-100 mb-4 mt-0">
        <div v-for="data in news" :key="data.id" class="row mb-3 box-news">
          <div class="col-md-4 p-0 d-flex">
              <img :src="data.urlToImage" alt="image_media">
          </div>  
          <div class="col-md-8 p-3 d-flex flex-column align-items-start justify-content-between information">
            <div class="w-100 d-flex flex-column justify-content-between" style="height:100%">
              <div>
                <h3><b>{{ data.title }}</b></h3>
                <p class="desc">{{ data.description }}</p>
              </div>
                <div class="d-flex justify-content-end align-items-end">
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
import SelectLanguage from '../components/LanguageSelect.vue'
import SortBy from '../components/SortBy.vue'
import Search from '../components/Search.vue'

export default {
  name: 'News',
  components : {
      SelectLanguage,
      SortBy,
      Search,
  },
  data(){
    return {
      news : [],
      data : {
        q : 'social',
        language : '',
        from : '',
        to : '',
        sortBy : '',
      }
    }
  },
  mounted(){
    this.getNews();
  },
  methods : {
    getNews(){
      axios.get('https://newsapi.org/v2/everything?q=' + this.data.q + '&language=' + this.data.language + '&from=' + this.data.from + '&to=' + this.data.to + '&sortBy='+ this.data.sortBy + '&apiKey=6c0c839f2c914a1ea4fbef97585da424').then((res)=>{
        this.news = res.data.articles;
      });
    },

    changeC(country){
        this.data.language = country;
        this.getNews();
    },
    
    changeSortBy(sortBy){
        this.data.sortBy = sortBy;
        this.getNews();
    },

    changeq(q){
      if(q == ''){
        this.data.q = 'social';
      }else{
        this.data.q = q;
      }
      this.getNews();
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import '../assets/css/news.css';
</style>