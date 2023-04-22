<template>
  <q-form @submit.prevent="searchMovies()">
    <q-input
      bottom-slots
      v-model="search"
      rounded
      outlined
      placeholder="What are you looking for?"
      :dense="dense"
    >
      <template v-slot:append>
        <q-icon
          v-if="search !== ''"
          name="close"
          @click="search = ''"
          class="cursor-pointer"
        />
        <q-icon name="search" />
      </template>
    </q-input>
  </q-form>
  <q-btn color="red" label="Search" class="btn" @click="searchMovies()" />

  <div class="container">
    <div class="row">
      <div
        class="col-xs-12 col-sm-12 col-md-6 col-lg-3"
        v-for="movie in movies"
        :key="movie.imdbID"
      >
        <router-link :to="'/movie/' + movie.imdbID">
          <q-card class="q-my-lg q-mx-md">
            <q-img :src="movie.Poster" alt="Movie Poster">
              <div class="absolute-bottom text-h6 text-center">
                {{ movie.Title }}
              </div>
            </q-img>
          </q-card>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import env from "../env.js";

export default {
  name: "Search",

  setup() {
    const search = ref("");
    const movies = ref([]);

    const searchMovies = () => {
      if (search.value != "") {
        fetch(`https://www.omdbapi.com/?apikey=${env.apikey}&s=${search.value}`)
          .then((response) => response.json())
          .then((data) => {
            movies.value = data.Search;
            search.value = "";
          });
      }
    };

    return {
      ph: ref(""),
      dense: ref(false),
      search,
      movies,
      searchMovies,
    };
  },
};
</script>

<style scoped>
.btn {
  margin: 5px 40% auto;
}
</style>

