
<template>
  
  <div class="d-flex flex-column align-items-start w-100">
    <input type="text" v-model="data.q" class="form-control input" placeholder="Search" v-on:keyup="getq()">
  </div>

</template>

<script>
export default {
  name: 'Search',
  data(){
      return {
          data : {
              q : ""
          }
      }
  },
  methods : {
    getq(){
        this.$emit('changeq', this.data.q);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.input{
    border-radius: 20px;
}
</style>
