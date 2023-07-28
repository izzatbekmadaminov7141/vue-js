<template>
  <div>
    <input
      type="text"
      class="form-control search-ponel"
      placeholder="Kino qidruv ..."
      @input="changeHandler"
      :value="temp"
    />
  </div>
</template>
<script>
export default {
  props: {
    updateTempHandle: {
      type: Function,
      required: true,
    },
  },
  data() {
    return {
      temp: "",
    };
  },
  methods: {
    changeHandler(e) {
      this.temp = e.target.value;
      this.updateTempHandle(this.temp);
    },
  },
};
</script>
<style>
.search-ponel {
  padding: 10px;
  margin: 10px 0;
}
</style>
