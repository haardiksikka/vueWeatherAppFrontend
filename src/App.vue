<template>
  
  <div id="app">
    <Navbar> </Navbar>
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HomePage msg="Welcome to Your Vue.js App"/> -->
    <div class="wrapper">
   <div class="widget" style="color:grey">
      <h1 style="text-align:center; color:white;">Weather Forecast</h1>
        <p style="text-align: center; color:white">Search Weather forecast of your region in just one click</p><br><br>

        <HomePage></HomePage> 
    </div>
  </div> 
    <Footer></Footer>
  </div>
</template>

<script>
import HomePage from './home/HomePage.vue';
import Footer from './footer/footer.vue';
import Navbar from './navbar/navbar.vue'
export default {
  name: 'app',
  components: {
    HomePage,
    Footer,
    Navbar,
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}
.wrapper{
    background-image: url('http://3.bp.blogspot.com/-kAiQOlaYlQk/UAfIqpSLfJI/AAAAAAAAFt0/YsT0grBr8zM/s640/2C2B0128-1024.jpg');
    background-attachment: fixed;
    background-repeat: no-repeat;
    background-size: cover;
    padding-bottom:100px;
    padding-top:100px;
}


.widget{
    background-color:rgba(0,0,0,0.7);
    border-radius:16px;
    padding:20px;
}

</style>
