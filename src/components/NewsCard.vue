<template>

    <div class="col-md-12 col-sm-9 col-11 m-0 d-flex justify-content-start">
         <h2><b>Today News</b></h2>
    </div> 
    <div class="container col-md-12 col-sm-11 col-12"> 
        <div v-for="data in news.slice(0, 4)" :key="data.id" class="ms-0 row mt-3 box-news">
                <div class="col-md-4 p-0 d-flex">
                    <img :src="data.urlToImage" class="p-0" alt="">
                </div>
                <div class="col-md-8 p-3 d-flex flex-column align-items-start justify-content-between information">
                    <h4><b>{{ data.title }}</b></h4>
                    <p class="desc">{{ data.description }}</p>
                    <div class="d-flex justify-content-end mt-0">
                        <a :href="data.url" target="_blank"><button class="btn btn-secondary btn-sm mb-1">Go To Article</button></a>
                    </div>
                   
                    <div class="card-footer col-12 d-flex justify-content-end text-muted">
                        <h6 class="m-0 newscard-date">{{ data.publishedAt }}</h6>
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
          axios.get('https://newsapi.org/v2/everything?qlnTitle=' + this.data.qlnTitle + '&q='+ this.data.q +'&language=' + this.data.language + '&sortBy=' + this.data.sortBy +'&apiKey=3da6743a387446a9a4fd10fbdd1ca0e0').then((res)=>{
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
