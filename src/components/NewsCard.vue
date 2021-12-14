<template>

    <div class="col-md-12 col-sm-9 col-11 m-0 d-flex justify-content-between">
         <h2 class="m-0"><b>Today News</b></h2>
         <div class="d-flex justify-content-around">
            <SelectLanguage @changeLanguage="changeC($event)" />
        </div>
    </div> 
    <div class="container col-md-12 col-sm-11 col-12"> 
        <div v-for="data in news.slice(0, 4)" :key="data.id" class="ms-0 row mt-3 box-news">
                <div class="col-md-4 p-0 d-flex">
                    <img :src="data.urlToImage" class="p-0" alt="">
                </div>
                <div class="col-md-8 p-3 d-flex flex-column align-items-start justify-content-between information">
                    <h3><b>{{ data.title }}</b></h3>
                    <p class="desc">{{ data.description }}</p>
                    <div class="d-flex justify-content-end">
                        <a :href="data.url" target="_blank"><button class="btn btn-secondary btn-sm mb-1">Go To Article</button></a>
                    </div>
                   
                    <div class="card-footer col-12 d-flex justify-content-end text-muted">
                        <h6 class="m-0">{{ data.publishedAt }}</h6>
                    </div> 
                </div>   
            </div>
    </div>

</template>

<script>
import SelectLanguage from '../components/LanguageSelect.vue'

export default {
  name: 'NewsCard',
  components : {
      SelectLanguage,
  },
  data(){
    return {
        news : [],
        data : {
            qInTitle : '',
            q : 'social',
            sources : '',
            language : '',
            sortBy : 'publishedAt'
        }
    }
  },
  mounted(){
      this.getNews();
  },
  methods : {
      getNews(){
          axios.get('https://newsapi.org/v2/everything?qInTitle=' + this.data.qInTitle + '&sources=' + this.data.sources + '&q='+ this.data.q +'&language=' + this.data.language + '&sortBy=' + this.data.sortBy +'&apiKey=eda27adfc6684982bba599abb733e9d4').then((res)=>{
              this.news = res.data.articles;
          }).catch(err=>{
              console.error(err);
          })
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
.box-news{
    width: 100%;
}

.btn-information button{
    color:white;
}
.box-news{
    background-color:#f8f8f8;
    border-color: black;
    box-shadow: 2px 4px 5px 0px rgba(0, 0, 0, 0.116);
}

.information h3{
    text-align: left;
}

.box-news .information .desc{
    text-align: left;
}

.information .date{
    width: 100%;
}

.box-news img{
    width: 100%;
    height: 100%;
    padding:10px;
}

</style>
