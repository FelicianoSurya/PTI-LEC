
<template>
  
  <div>
  
    <select v-model="this.data.country" class="form-select" @change="getCountry()">
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
  mounted(){
      this.getCountry();
  },
  methods : {
    getCountry(){
        this.$emit('changeCountry', this.data.country);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
