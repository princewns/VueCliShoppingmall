<template>
  <div id="app">
    <ProductDisplay/>
    <ReviewForm v-on:submit-review="addReview"/>
    <ReviewList v-bind:reviews="reviews"/>
  </div>
</template>

<script>
import ProductDisplay from './components/ProductDisplay.vue';
import ReviewForm from './components/ReviewForm.vue';
import ReviewList from './components/ReviewList.vue';


export default {
  name : 'App',
  components : {
    ProductDisplay,
    ReviewForm,
    ReviewList
  },
  data : function(){
    return {reviews : []}
    },
            
  methods : {
    addReview : function(review){
    this.reviews.push(review);
    }
  }
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
body {
  background-color: #f2f2f2;
  margin: 0px;
  font-family: tahoma;
  color: #282828;
}
</style>
