<template>
  <hello-world />
  <!-- <Index /> -->
</template>

<script>
import HelloWorld from "../components/HelloWorld";
import Index from "../components/index";

export default {
  name: "home",
  components: {
    HelloWorld,
    // index,
  },
};
</script>
