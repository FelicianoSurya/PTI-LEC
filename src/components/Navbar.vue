<template>
  
    <div class="container-fluid p-0" style="background-color:black">
        <div class="nav p-0 d-flex justify-content-center align-items-center">
            <ul class="col-lg-5 col-11 d-flex m-0">
                <li class="nav-item px-3">
                    <a class="nav-link"><router-link to="/">Home</router-link></a>
                </li>
                <li class="nav-item px-3">
                    <a class="nav-link"><router-link to="/news">Headlines</router-link></a>
                </li>
                <li class="nav-item px-3">
                    <a class="nav-link"><router-link to="/news">News</router-link></a>
                </li>
                <li class="nav-item px-3">
                    <a class="nav-link"><router-link to="/about">About Us</router-link></a>
                </li>
            </ul>
        </div> 
    </div>

</template>

<script>
export default {
  name: 'Navbar',
  data(){
    return {
      isList : 0,
    }
  },
  mounted(){
      
  },
  methods : {
    
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import '../assets/css/news.css';
</style>
