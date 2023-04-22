<template>
  <div class="q-pa-md">
    <q-carousel
      animated
      v-model="slide"
      navigation
      infinite
      :autoplay="autoplay"
      arrows
      transition-prev="slide-right"
      transition-next="slide-left"
      @mouseenter="autoplay = false"
      @mouseleave="autoplay = true"
    >
      <q-carousel-slide
        :name="1"
        img-src="https://justfields.com/storage/projects/7M5rV059/dark.jpg"
      >
        <div class="absolute-bottom custom-caption">
          <div class="text-h2">The Dark Knight</div>
          <div class="text-subtitle1">
            Directed by Christopher Nolan. With Christian Bale, Heath Ledger,
            Aaron Eckhart, Michael Caine. When the menace known as the Joker
            wreaks.
          </div>
        </div>
      </q-carousel-slide>
      <q-carousel-slide
        :name="2"
        img-src="https://justfields.com/storage/projects/7M5rV059/naruto.jpg"
      >
        <div class="absolute-bottom custom-caption">
          <div class="text-h2">Naruto</div>
          <div class="text-subtitle1">
            A Japanese manga series written and illustrated by Masashi
            Kishimoto. It tells the story of Naruto Uzumaki, a young ninja who
            seeks recognition.
          </div>
        </div>
      </q-carousel-slide>
      <q-carousel-slide
        :name="3"
        img-src="https://justfields.com/storage/projects/7M5rV059/joker.jpg"
      >
        <div class="absolute-bottom custom-caption">
          <div class="text-h2">Joker</div>
          <div class="text-subtitle1">
            Directed by Todd Phillips. With Joaquin Phoenix, Robert De Niro,
            Zazie Beetz, Frances Conroy. The rise of Arthur Fleck, from aspiring
            stand-up.
          </div>
        </div>
      </q-carousel-slide>
      <q-carousel-slide
        :name="4"
        img-src="https://justfields.com/storage/projects/7M5rV059/one.jpg"
      >
        <div class="absolute-bottom custom-caption">
          <div class="text-h2">One Piece</div>
          <div class="text-subtitle1">
            A Japanese manga series written and illustrated by Eiichiro Oda. It
            has been serialized in Shueisha's shōnen manga.
          </div>
        </div>
      </q-carousel-slide>
    </q-carousel>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "Carousel",

  setup() {
    return {
      slide: ref(1),
      autoplay: ref(true),
    };
  },
};
</script>

<style lang="sass" scoped>
.custom-caption
  text-align: center
  padding: 12px
  color: white
  background-color: rgba(0, 0, 0, .3)
</style>
