<template>
  <div class="home">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <bar />
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";
import Bar from "@/components/Bar.vue";

export default {
  name: "home",
  components: {
    // HelloWorld,
    Bar
  }
};
</script>
