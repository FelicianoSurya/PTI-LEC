<template>   


    <div class="container-fluid pt-4 col-lg-11">
        <div v-for="data in headlines.slice(0, 1)" :key="data.id" class="background-banner d-flex flex-column justify-content-between" v-bind:style="{ backgroundImage : 'url(' + data.urlToImage + ')' }">
            <div class="col-lg-12 p-2 d-flex justify-content-end">
                <div class="col-2" placeholder="Language">
                    <SelectCountry @changeCountry="changeC($event)" />
                </div>
            </div>
            <div class="w-100 h-100 px-4 py-2 d-flex flex-column background-title">
                <h4><b>{{ data.title }}</b></h4>
                <p>{{ data.description }}</p>
                <div class="headline-date d-flex justify-content-start">
                    <p>{{ data.publishedAt }}</p>
                </div>
                <div class="d-flex justify-content-start col-lg-7">
                    <a :href="data.url" target="_blank" class="col-2"><button class="btn btn-danger btn-sm">Go To Article</button></a>
                </div>
            </div>
        </div>
         <div class="col-lg-12 pt-2 d-flex justify-content-end">
            <router-link to=""><button class="btn btn-danger">More Headline</button></router-link>
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
    @import '../assets/css/slide.css';
</style>
