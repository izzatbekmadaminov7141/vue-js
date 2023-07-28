<template>
  <div>
    <MovieListItem
      v-for="movie in movies"
      :movie="movie"
      :key="movie.id"
      @onToggle="$emit('onToggle', $event)"
      @onRemove="$emit('onRemove', movie.id)"
    />
  </div>
</template>

<script>
import MovieListItem from "@/components/movie-list-item/MovieListItem.vue";
export default {
  components: {
    MovieListItem,
  },
  props: {
    movies: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped></style>
