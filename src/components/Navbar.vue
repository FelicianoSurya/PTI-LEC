<template>
  
    <div class="container-fluid p-0" style="background-color:black">
        <div class="nav p-2 d-flex justify-content-center align-items-center">
            <ul class="col-lg-5 col-11 d-flex m-0">
                <li class="nav-item pe-3">
                    <a class="nav-link"><router-link to="/">Home</router-link></a>
                </li>
                <li class="nav-item px-3">
                    <a class="nav-link"><router-link to="/news">News</router-link></a>
                </li>
                <li class="nav-item px-3">
                    <a class="nav-link"><router-link to="/about">About Us</router-link></a>
                </li>
            </ul>
            <div class="col-lg-6 col-xs-10 search d-flex justify-content-end pe-4">
                <div class="col-lg-5">
                    <input placeholder="Search" type="text" class="input form-control flex-column">   
                </div><a class="px-1" href="#">
              <img alt=" " src="../assets/images/search.png">
            </a>
            </div> 
            
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
