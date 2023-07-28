<template>
  <div class="movie_add-form">
    <h3>Yangi kino qo'shish:</h3>
    <form class="add-form d-flex" @submit.default>
      <input
        type="text"
        class="form-control new-movie-lable"
        placeholder="Qanday kino ?"
        :value="name"
        @input="name = $event.target.value"
      />
      <input
        type="text"
        class="form-control new-movie-lable"
        placeholder="necha marta ko'rilgan ?"
        :value="viwers"
        @input="viwers = $event.target.value"
      />
      <PrimaryButton
        class="btn btn-outline-dark"
        type="submit"
        @click="addMovie"
      >
        Qo'shish
      </PrimaryButton>
    </form>
  </div>
</template>

<script>
import PrimaryButton from "../ui-components/PrimaryButton.vue";
export default {
  components: {
    PrimaryButton,
  },
  data() {
    return {
      name: "",
      viwers: "",
    };
  },
  methods: {
    addMovie() {
      const newMovie = {
        name: this.name,
        viwers: this.viwers,
        fovorite: false,
        like: false,
        id: Date.now(),
      };
      this.$emit("addMovies", newMovie);
      this.name = "";
      this.viwers = "";
    },
  },
};
</script>

<style scoped>
.new-movie-lable {
  background-color: #fff;
  border-radius: 5px;
  box-sizing: 15px 15px 15px rgba(0, 0, 0, 0.15);
  padding: 10px;
  margin-right: 10px;
}
</style>
