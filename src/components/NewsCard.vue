<template>

    <div class="col-md-12 col-sm-9 col-11 m-0 d-flex flex-column justify-content-start mt-3">
        <div class="d-flex justify-content-between">
            <h2><b>Today News</b></h2>
            <LanguageSelect @changeLanguage="changeLanguage($event)" />
        </div>
        <hr class="w-100 mt-1 mb-2">
    </div> 
    <div class="container col-md-12 col-sm-11 col-12"> 
        <div v-for="data in news.slice(0, limit)" :key="data.id" class="ms-0 row mt-3 box-news">
                <div class="col-md-4 p-2 d-flex">
                    <img :src="data.urlToImage" class="p-0" alt="">
                </div>
                <div class="col-md-8 p-3 d-flex flex-column align-items-start justify-content-between information">
                    <h4><b>{{ data.title }}</b></h4>
                    <p class="desc">{{ data.description }}</p>

                    <div class="d-flex justify-content-end">
                        <a :href="data.url" target="_blank"><button class="btn btn-secondary btn-sm mb-1">Go To Article</button></a>
                    </div>

                    <div class="card-footer col-12 d-flex justify-content-end text-muted">
                        <h6 class="m-0 newscard-date">{{ data.publishedAt }}</h6>
                    </div> 
                </div>   
            </div>
            <div class="d-flex justify-content-end pt-3">
                <button v-if="limit < 10" class="btn btn-dark" @click="moreNews()">More News</button>
                <router-link to="/news"><button v-if="limit >= 10" class="btn btn-primary">News Page</button></router-link>
            </div>
    </div>

</template>

<script>
import LanguageSelect from '../components/LanguageSelect.vue'

export default {
  name: 'NewsCard',
  components : {
      LanguageSelect,
  },
  data(){
    return {
        news : [],
        limit : 4,
        x : 0,
        plus : [4,2],
        data : {
            qlnTitle : '',
            q : 'social',
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
          axios.get('https://newsapi.org/v2/everything?qlnTitle=' + this.data.qlnTitle + '&q='+ this.data.q +'&language=' + this.data.language + '&sortBy=' + this.data.sortBy +'&apiKey=81d9902f3c134af59184159644223273').then((res)=>{
              this.news = res.data.articles;
          });
      },
      changeLanguage(language){
          this.data.language = language;
          this.getNews();
      },
      moreNews(){
          this.limit = this.limit + this.plus[this.x];
          this.x = this.x + 1;
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

.information h4{
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

.newscard-date {
    font-size: 12px;
}

</style>
