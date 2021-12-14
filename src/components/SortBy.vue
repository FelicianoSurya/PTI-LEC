
<template>
  
  <div class="d-flex flex-column align-items-start">
    <select v-model="this.data.sortBy" class="form-control" @change="getsortBy()">
        <option value="">Sort By</option>
        <option value="publishedAt">Publised At</option>
        <option value="popularity">Popularity</option>
    </select>

  </div>

</template>

<script>
export default {
  name: 'SortBy',
  data(){
      return {
          data : {
              sortBy : ""
          }
      }
  },
  mounted(){
      this.getsortBy();
  },
  methods : {
    getsortBy(){
        this.$emit('changeSortBy', this.data.sortBy);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
