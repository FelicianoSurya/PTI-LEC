<template>
  
  <div>
      
    <div v-for="data in news.slice(0, 4)" :key="data.id" class="row m-3">
        <div class="col-12 p-0 w-100 box-news d-flex">
            <div class="col-4 p-0">
                <img :src="data.urlToImage" class="p-0" alt="">
            </div>
            <div class="col-md-8 p-3 d-flex flex-column align-items-start justify-content-between information">
            <div>
              <h3><b>{{ data.title }}</b></h3>
              <p class="desc">{{ data.description }}</p>
              <div class="d-flex justify-content-end btn-information">
                  <a :href="data.url" target="_blank"><button class="btn btn-info m-3">Go To Article</button></a>
              </div>
            </div>
            <div class="card-footer col-12 d-flex justify-content-end text-muted">
                <h6 class="m-0">{{ data.publishedAt }}</h6>
            </div> 
          </div>
        </div>
    </div>

  </div>

</template>

<script>
export default {
  name: 'NewsCard',
  data(){
    return {
        news : [],
        data : {
            qlnTitle : '',
            q : 'all',
            language : '',
            sortBy : ''
        }
    }
  },
  mounted(){
      this.getNews();
  },
  methods : {
      getNews(){
          axios.get('https://newsapi.org/v2/everything?qlnTitle=' + this.data.qlnTitle + '&q='+ this.data.q +'&language=' + this.data.language + '&sortBy=' + this.data.sortBy +'&apiKey=9df00cedc1d04fb99e0e61c94c9f52da').then((res)=>{
              this.news = res.data.articles;
          });
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
