
<template>
  
  <div>
  
    <select v-model="this.data.country" class="form-control" @change="getHeadline()">
        <option value="us">US</option>
        <option value="ae">United Arab Emirates</option>
        <option value="ar">Argentina</option>
        <option value="at">Austria</option>
        <option value="au">Australia</option>
        <option value="be">Belgium</option>
        <option value="bg">Bulgaria</option>
        <option value="br">Brazil</option>
        <option value="ca">Canada</option>
        <option value="ch">Switzerland</option>
        <option value="cn">China</option>
        <option value="id">Indonesia</option>
    </select>

  </div>

</template>

<script>
export default {
  name: 'CountrySelect',
  data(){
      return {
          data : {
              country : "id"
          }
      }
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

</style>
