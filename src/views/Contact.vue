<template>
  <div class="home">
    <div class="container">
      <h1>Contact</h1>
      <div class="row">
        <div class="col">
          <h4>Address</h4>
          <ul>
            <li>
              197
              Thornbury Crescent
            </li>
            <li>
              Nepean ON K2G6C2
              Canada
            </li>
            <li>514-691-4177</li>
          </ul>
        </div>
        <div class="col">
          <h4>Hours of Operation</h4>
          <ul>
            <!-- array用for...of，object用for...in -->
            <li v-for="hour of hours">{{ hour.day }}: {{ hour.time }}</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      hours: [
        { day: "Monday", time: "8AM-6PM" },
        { day: "Tuesday", time: "8AM-6PM" },
        { day: "Wednesday", time: "8AM-6PM" },
        { day: "Thursday", time: "8AM-6PM" },
        { day: "Friday", time: "8AM-5PM" },
        { day: "Saturday", time: "10AM-4PM" },
        { day: "Sunday", time: "10AM-2PM" }
      ]
    };
  }
};
</script>
<style>
.col {
  text-align: left;
}

ul {
  padding-left: 0;
}

ul li {
  list-style: none;
}
</style>