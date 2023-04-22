<template>
  <div class="container text-center">
    <div class="row">
      <div class="col">
        <h2 class="text-h3">{{ movie.Title }}</h2>

        <q-chip outline color="teal" class="text-h6">
          {{ movie.Year }}
        </q-chip>
        <q-img :src="movie.Poster" class="img" />
        <p class="text-body2">{{ movie.Plot }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, onBeforeMount } from "vue";
import { useRoute } from "vue-router";
import env from "../env.js";

export default {
  name: "MovieDetails",

  setup() {
    const movie = ref({});
    const route = useRoute();

    onBeforeMount(() => {
      fetch(
        `https://www.omdbapi.com/?apikey=${env.apikey}&i=${route.params.id}&plot=full`
      )
        .then((response) => response.json())
        .then((data) => {
          movie.value = data;
        });
    });

    return {
      movie,
    };
  },
};
</script>

<style scoped>
.img {
  display: block;
  max-width: 250px;
  margin-bottom: 16px;
  margin-left: auto;
  margin-right: auto;
  margin-top: 12px;
}
</style>
