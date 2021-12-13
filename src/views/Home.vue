<template>
  <div class="home">
   
  <Slide />

  <div class="container mt-5">
    <div class="row">
      <news-card />
    </div>
  </div>

  </div>
</template>

<script>
// @ is an alias to /src
import Slide from '../components/Slide'
import NewsCard from '../components/NewsCard.vue'

export default {
  name: 'Home',
  components: {
    Slide,
    NewsCard
  }
}
</script>
