<template>
  <div id="app">
    <!-- nav -->
    <div class="navbar" style="background-color: #e3f2fd;">
      <div class="container">
        <a class="navbar-brand" style="color:black; padding-left:0" href="#">My Vue App</a>
        <nav class="nav">
          <router-link to="/">Home</router-link>
          <router-link to="about">About</router-link>
          <router-link to="contact">Contact</router-link>
          <router-link to="testimonials">User Testimonials</router-link>
        </nav>
      </div>
    </div>
    <!-- end of nav -->
    <router-view />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "app",
  components: {
    HelloWorld
  },
  computed: {
    title: function() {
      return "My Vue App";
    }
  }
};
</script>

<style>
#app {
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.navbar {
  font-size: 20px;
  align-items: center;
  background-color: hsl(0, 0%, 97%);
  display: flex;
  height: 60px;
}

a {
  padding-left: 20px;
}
</style>
