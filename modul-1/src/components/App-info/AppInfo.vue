<template>
  <div class="app-info">
    <p class="fs-3 text-uppercase">
      Barcha kinolar soni: {{ allMOvieCounter }}
    </p>
    <p class="fs-4 text-uppercase">
      Ko'rilgan kinolar soni : {{ allMovieFovorite }}
    </p>
  </div>
</template>
<script>
export default {
  props: {
    allMOvieCounter: {
      type: String,
      required: true,
    },
    allMovieFovorite: {
      type: String,
      required: true,
    },
  },
};
</script>
<style scoped>
.app-info {
  padding: 10px;
}
</style>
