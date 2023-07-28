<template>
  <div class="bg-dark bg-height p-5">
    <h1 class="text-center text-light">Movie Page:</h1>
    <div class="card_information bg-light">
      <AppInfo />
      <MovieSearch />
    </div>
  </div>
</template>

<script>
import AppInfo from "@/components/App-info/AppInfo.vue";
import MovieSearch from "@/components/MovieSearch/MovieSearch.vue";
export default {
  components: {
    AppInfo,
    MovieSearch,
  },
};
</script>

<style scoped>
.bg-height {
  height: 100vh;
}
.card_information {
  width: 60vw;
  margin: 0 auto;
  min-height: 30vh;
  border-radius: 20px;
  padding: 20px;
}
</style>
