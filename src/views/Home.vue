<template>
  <div class="home">
    <div class="container">
      <h1>Welcome to My Vue App</h1>
      <div class="row">
        <div class="col">
          <img alt="me" src="../assets/cartoon_icon.jpeg" />
        </div>
        <div class="col">
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce at eleifend enim. Fusce tempus pulvinar dui laoreet vestibulum. Ut nec mattis nibh. Nullam et lobortis magna, in molestie arcu. Quisque ac ipsum ut leo imperdiet facilisis non vel orci. Curabitur porta ipsum quis justo fringilla volutpat. Aliquam dapibus tempus urna, in luctus justo. Quisque purus ipsum, ultricies non consequat ac, elementum a mauris. Duis vitae dui purus. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Sed volutpat tincidunt dui nec pellentesque. Nunc nunc dui, faucibus ut blandit malesuada, vehicula ac ipsum.</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "home",
  components: {
    HelloWorld
  }
};
</script>

<style>
h1 {
  text-align: left;
  margin-top: 1rem;
}

.row {
  margin-top: 20px;
}
.col:nth-child(2) {
  text-align: left;
}
</style>
