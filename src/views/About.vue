<template>

  <div class="container-fluid col-lg-12 d-flex about-top p-5 row">
    <div class="col-lg-5 justify-content-center align-items-center py-5">
        <img src="../assets/images/logo1.png" alt="">
    </div> 
    <div class="col-lg-7 pe-3 py-5" style="text-align:left">
      <h3><b>About World E-News</b></h3>
      <p>World E-News is a website that helps you to be able to read and find out the latest news
         globally in several countries in the world. This website has features that make it easier for users to find the news they want.<br>
          This website is also created using the Angular Framework and News API from https://newsapi.org/ site.
      </p>
    </div>
  </div>

  <div class="container-fluid p-0">
    <div class="section-6 py-5 about-top1" id="team">
      <div class="container pt-3 pb-5">
          <div class="row justify-content-center">
              <h2 class="pb-3"><b>Available Features</b></h2>
              <div class="col-lg-2 col-sm-6 col-9 p-lg-0 mx-2 mt-3">
                  <div class="ourteam-card text-center bg-white">
                      <img src="https://img.icons8.com/ios/100/000000/news.png" alt="" class="img1">
                      <h6><b>Headline</b></h6>
                      <p style="font-size:12px">Providing the best news with a worlwide scope.</p> 
                  </div>
              </div>
                 <div class="col-lg-2 col-sm-6 col-9 p-lg-0 mx-2 mt-3">
                  <div class="ourteam-card text-center bg-white">
                      <img src="https://img.icons8.com/ios/100/000000/line-chart--v1.png" alt="" class="img1" >
                      <h6><b>Trending News</b></h6>
                      <p style="font-size:12px">Providing the most popular news among people.</p>                   
                  </div>
              </div>
               <div class="col-lg-2 col-sm-6 col-9 p-lg-0 mx-2 mt-3">
                  <div class="ourteam-card text-center bg-white">
                      <img src="https://img.icons8.com/ios/100/000000/sort-window.png" alt="" class="img1">
                      <h6><b>Filter</b></h6>
                      <p style="font-size:12px">Filtering news according to the desired criteria.</p>                      
                  </div>
              </div>
               <div class="col-lg-2 col-sm-6 col-9 p-lg-0 mx-2 mt-3">
                  <div class="ourteam-card text-center bg-white">
                      <img src="https://img.icons8.com/ios/100/000000/today.png" alt="" class="img1">
                      <h6><b>Today News</b></h6>
                      <p style="font-size:12px">Providing the latest news with a worlwide scope.</p> 
                  </div>
              </div>
               <div class="col-lg-2 col-sm-6 col-9 p-lg-0 mx-2 mt-3">
                  <div class="ourteam-card text-center bg-white">
                      <img src="https://img.icons8.com/ios/100/000000/window-search.png" alt="" class="img1">
                      <h6><b>Search</b></h6>
                      <p style="font-size:12px">Makes it easy to search for global news.</p> 
                  </div>
              </div>
            </div>
        </div>
    </div>
  </div>

   <div class="container-fluid p-0 pt-3">
    <div class="section-6 py-5" id="team">
      <div class="container">
          <div class="row justify-content-center">
              <div class="px-5 mb-2">
                <h2 class="mb-4"><b>Meet The Tiny Team</b></h2>
                    <p> Hello there! introduce us as The Tiny Team that consist of 3 people who are currently studying 
                        at Multimedia Nusantara University, Informatics Major, Class of 2020. We created this website 
                        as a fulfillment of the 3rd semester final exam in the Introduction to Internet Technology course.
                    </p>
                <hr class="w-100">
                </div>
              <div class="col-lg-3 col-sm-6 col-8 p-3">
                  <div class="ourteam-card text-center img2">
                      <img src="../assets/images/Ano.png" alt="">
                      <h4><b>Feliciano Surya M</b></h4>
                      <p style="font-size:12px">feliciano.marcello@student.umn.ac.id</p> 
                      <p class="m-0">( 000 000 43255 )</p>
                  </div>
              </div>
              <div class="col-lg-3 col-sm-6 col-8 p-3">
                  <div class="ourteam-card text-center img2">
                      <img src="../assets/images/Dea.png" alt="">
                      <h4><b>Dea Noveriyanti</b></h4>
                      <p style="font-size:12px">dea.noveriyanti@student.umn.ac.id</p> 
                      <p class="m-0">( 000 000 42550 )</p>
                  </div>
              </div>
              <div class="col-lg-3 col-sm-6 col-8 p-3">
                  <div class="ourteam-card text-center img2">
                      <img src="../assets/images/Charisma.png" alt="">
                      <h4><b>Charisma Christ A</b></h4>
                      <p style="font-size:12px">charisma.anugrah@student.umn.ac.id</p> 
                      <p class="m-0">( 000 000 43903 )</p>
                  </div>
              </div>
            </div>
        </div>
    </div>
  </div>

</template>

<script>
export default {
  name: 'About',
  props: {
   
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import '../assets/css/aboutus.css';
</style>