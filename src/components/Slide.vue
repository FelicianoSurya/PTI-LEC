<template>
  
  <div>
      
    <div class="container-fluid p-0">
        <div v-for="data in headlines.slice(0, 1)" :key="data.id" class="background-banner d-flex flex-column justify-content-between align-items-center" v-bind:style="{ backgroundImage : 'url(' + data.urlToImage + ')' }">
            <div class="col-12 p-2 d-flex justify-content-end">
                <div class="col-1">
                    <router-link to=""><button class="btn btn-danger">More Headline</button></router-link>
                </div>
                <div class="col-1">
                    <SelectCountry @changeCountry="changeC($event)" />
                </div>
            </div>
            <div class="w-100 h-100 px-5 py-2 d-flex flex-column align-items-center background-title">
                <h3>{{ data.title }}</h3>
                <p>{{ data.publishedAt }}</p>
                <p>{{ data.description }}</p>
                <a :href="data.url" target="_blank" class="col-2"><button class="btn btn-danger">Go To Article</button></a>
            </div>
        </div>
    </div>
  </div>

</template>

<script>
import SelectCountry from '../components/CountrySelect.vue'

export default {
  name: 'Slide',
  components : {
      SelectCountry,
  },
  data(){
    return {
        headlines : [],
        data : {
            country : "us",
        }
    }
  },
  mounted(){
      this.getHeadline();
  },
  methods : {
      getHeadline(){
          axios.get('https://newsapi.org/v2/top-headlines?country=' +  this.data.country  + '&apiKey=9df00cedc1d04fb99e0e61c94c9f52da').then((res)=>{
              this.headlines = res.data.articles;
          });
      },
      changeC(country){
          this.data.country = country;
          this.getHeadline();
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.background-banner{
    width: 100%;
    min-height: 700px;
    background-size: cover;
    background-repeat:no-repeat ;
}

.background-title{
    background-color: rgba(0,0,0,0.5);
    color:white;
}
</style>
