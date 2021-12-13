<template>
  
  <div>
      
    <div class="container-fluid p-0">
        <div v-for="data in headlines.slice(0, 1)" :key="data.id" class="background-banner d-flex flex-column justify-content-between align-items-center" v-bind:style="{ backgroundImage : 'url(' + data.urlToImage + ')' }">
            <div class="col-12 p-2 d-flex justify-content-end">
                <div class="col-1">
                    <SelectCountry />
                </div>
            </div>
            <div class="w-100 h-100 px-5 py-2 d-flex flex-column background-title">
                <h3>{{ data.title }}</h3>
                <p>{{ data.publishedAt }}</p>
                <p>{{ data.description }}</p>
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
            country : "id",
        }
    }
  },
  mounted(){
      this.getHeadline();
  },
  methods : {
      getHeadline(){
          axios.get('https://newsapi.org/v2/top-headlines?country=' +  this.data.country  + '&apiKey=ae0db9c4ef714ec18ff33f2dccb5a2ee').then((res)=>{
              this.headlines = res.data.articles;
          });
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
