<template>

<div>

    <div class="container mt-2 col-md-11 col-sm-9 col-11">
        <div class="d-flex justify-content-end">
          <div class="d-flex justify-content-around p-3">
            <SelectLanguage @changeLanguage="changeC($event)" />
            <SortBy @changeSortBy="changeSortBy($event)" />
            <Search @changeq="changeq($event)" />
          </div>
        </div>
        <div v-for="data in news" :key="data.id" class="row mt-5 box-news">
          <div class="col-md-4 p-0 d-flex">
              <img :src="data.urlToImage" alt="image_media">
          </div>  
          <div class="col-md-8 p-3 d-flex flex-column align-items-start justify-content-between information">
            <div>
              <h3><b>{{ data.title }}</b></h3>
              <p class="desc">{{ data.description }}</p>
            </div>
            <div class="card-footer col-12 d-flex justify-content-end text-muted">
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
      axios.get('https://newsapi.org/v2/everything?q=' + this.data.q + '&language=' + this.data.language + '&from=' + this.data.from + '&to=' + this.data.to + '&sortBy='+ this.data.sortBy + '&apiKey=c43b4de0624d496890c10dec833b7275').then((res)=>{
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
      this.data.q = q;
      this.getNews();
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import '../assets/css/news.css';
</style>