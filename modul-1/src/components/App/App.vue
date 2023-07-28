<template>
  <div class="app">
    <div class="app_info">
      <AppInfo
        :allMOvieCounter="movies.length"
        :allMovieFovorite="movies.filter((e) => e.fovorite).length"
      />
    </div>
    <div class="searchPanel">
      <Search :updateTempHandle="updateTempHandle" />
      <AppFilter :updataFilter="updateFilter" :filterName="filter" />
    </div>
    <div class="movie">
      <MovieList
        :movies="onFilterHandle(onSearchHandle(movies, temp), filter)"
        @onToggle="onToggleHandleClick"
        @onRemove="onRemoveHandle"
      />
      <MovieAddForm @addMovies="addMovies" />
    </div>
  </div>
</template>

<script>
import AppInfo from "@/components/App-info/AppInfo.vue";
import Search from "@/components/search-ponel/Search.vue";
import AppFilter from "@/components/app-filter/AppFilter.vue";
import MovieAddForm from "@/components/movie-add-form/MovieAddForm.vue";
import MovieList from "@/components/movie-list/MovieList.vue";

export default {
  components: {
    AppInfo,
    Search,
    AppFilter,
    MovieAddForm,
    MovieList,
  },
  data() {
    return {
      movies: [
        {
          name: "Omar",
          viwers: "300",
          fovorite: false, // <--
          like: true, // <--
          id: 1,
        },
        {
          name: "Abdulhamid",
          viwers: "200",
          fovorite: true, // <--
          like: false, // <--
          id: 2,
        },
        {
          name: "Usmon ",
          viwers: "230",
          fovorite: true, // <--
          like: true, // <--
          id: 3,
        },
      ],
      temp: "",
      filter: "all",
    };
  },
  methods: {
    onFilterHandle(arr, filter) {
      switch (filter) {
        case "popular":
          return arr.filter((c) => c.like);
        case "mostViewers":
          return arr.filter((c) => c.viwers > 200);
        default:
          return arr;
      }
    },
    addMovies(item) {
      if (!item.name || !item.viwers) return;
      this.movies.push(item);
      console.log(item);
    },
    onToggleHandleClick({ id, prop }) {
      console.log(prop);
      this.movies = this.movies.map((item) => {
        if (item.id === id) {
          return { ...item, [prop]: !item[prop] };
        }
        return item;
      });
    },
    onRemoveHandle() {
      this.movies = this.movies.filter((item) => item.id !== id);
    },
    onSearchHandle(arr, temp) {
      if (temp.length === 0) {
        return arr;
      }
      return arr.filter((c) => c.name.toLowerCase().indexOf(temp) > -1);
    },

    updateTempHandle(temp) {
      this.temp = temp;
    },
    updateFilter(filter) {
      this.filter = filter;
    },
  },
};
</script>

<style>
.app {
  height: 100vh;
  background-color: #333;
  padding: 30px;
}
.app_info,
.searchPanel,
.movie {
  width: 1000px;
  margin: 20px auto;
  background-color: #fff;
  border-radius: 10px;
  padding: 10px 20px;
  box-shadow: 5px 4px 5px 1px rgb(181, 179, 179);
}
</style>
