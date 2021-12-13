<template>
  
  <div>
  
    <div class="container-fluid p-0" style="background-color:black">
        <div class="container nav p-2 d-flex justify-content-center align-items-center">
            <ul class="col-7 d-flex m-0 justify-content-around align-items-center">
                <li class="nav-item">
                    <a class="nav-link"><router-link to="/">Home</router-link></a>
                </li>
                <li class="nav-item">
                    <a class="nav-link"><router-link to="/blog">News</router-link></a>
                </li>
                <li class="nav-item">
                    <a class="nav-link"><router-link to="/development">About Us</router-link></a>
                </li>
                <li class="nav-item" v-show="isList" style="cursor:pointer">
                    <a class="nav-link" @click="logout()">Logout</a>
                </li>
            </ul>
            <div class="col-5 search d-flex justify-content-end">
                <div class="col-5">
                    <input type="text" class="input form-control">
                </div>
            </div>
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
