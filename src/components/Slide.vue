<template>   

        <div class="container-fluid pt-3 col-lg-11">
            <div v-for="data in headlines.slice(0, 1)" :key="data.id" class="background-banner d-flex flex-column justify-content-between" v-bind:style="{ backgroundImage : 'url(' + data.urlToImage + ')' }">
                <div class="col-lg-12 col-12 p-2 d-flex justify-content-end">
                    <div class="col-lg-2 col-sm-3" placeholder="Language">
                        <SelectCountry @changeCountry="changeC($event)" />
                    </div>
                </div>
                <div class="h-100 px-4 py-2 headline-desc flex-column justify-content-start text-left background-title">
                    <h4><b>{{ data.title }}</b></h4>
                    <p>{{ data.description }}</p>
                    <div class="headline-date d-flex justify-content-start newscard-date">
                        <p>{{ data.publishedAt }}</p>
                    </div>
                    <div class="d-flex justify-content-start col-lg-12 col-xs-11 mb-1">
                        <a :href="data.url" target="_blank" class="col-lg-3"><button class="btn btn-light btn-sm">Go To Article</button></a>
                    </div>
                </div>
            </div>
            <div class="col-lg-12 pt-2 d-flex justify-content-end">
                <router-link to="/trending"><button class="btn btn-dark">See More Trending News</button></router-link>
            </div>
        </div>


</template>

<script>
import SelectCountry from '../components/CountrySelect.vue'
// AOS.init();
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
          axios.get('https://newsapi.org/v2/top-headlines?country=' +  this.data.country  + '&apiKey=81d9902f3c134af59184159644223273').then((res)=>{
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
    /* @import 'https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css';
    @import 'https://unpkg.com/aos@2.3.1/dist/aos.css';
    @import 'https://unpkg.com/aos@2.3.1/dist/aos.js'; */

</style>

