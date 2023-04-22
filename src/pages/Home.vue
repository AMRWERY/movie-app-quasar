<template>
  <Carousel />
  <Search />
</template>

<script>
import Carousel from "src/components/Carousel.vue";
import Search from "src/components/Search.vue";

export default {
  name: "Home",

  components: { Carousel, Search },
};
</script>
