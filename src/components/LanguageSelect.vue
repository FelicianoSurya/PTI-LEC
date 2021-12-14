
<template>
  
  <div class="d-flex flex-column align-items-start w-100">
    <select v-model="this.data.language" class="form-select" @change="getLanguage()">
        <option value="">Country</option>
        <option value="de">Germany</option>
        <option value="ar">Argentina</option>
        <option value="es">Spain</option>
        <option value="fr">France</option>
        <option value="it">Italy</option>
        <option value="nl">Netherlands</option>
        <option value="br">Brazil</option>
        <option value="no">Norway</option>
        <option value="pt">Portugal</option>
        <option value="ru">Russia</option>
        <option value="se">Swedia</option>
    </select>

  </div>

</template>

<script>
export default {
  name: 'LanguageSelect',
  data(){
      return {
          data : {
              language : ""
          }
      }
  },
  mounted(){
      this.getLanguage();
  },
  methods : {
    getLanguage(){
        this.$emit('changeLanguage', this.data.language);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
