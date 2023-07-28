<template>
  <div class="btn-group">
    <PrimaryButton
      v-for="btn in filterButtons"
      :key="btn.name"
      :class="[filterName === btn.name ? 'btn-dark' : 'btn-outline-dark']"
      @click="filterHandle(btn.name)"
    >
      {{ btn.title }}
    </PrimaryButton>
  </div>
</template>
<script>
export default {
  props: {
    updataFilter: {
      type: Function,
      required: true,
    },
    filterName: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      filterButtons: [
        {
          title: "All",
          name: "all",
        },
        {
          title: "Populer",
          name: "popular",
        },
        {
          title: "most Viewers",
          name: "mostViewers",
        },
      ],
      filter: "all",
    };
  },
  methods: {
    filterHandle(filter) {
      this.filter = filter;
      this.updataFilter(this.filter);
    },
  },
};
</script>
<style></style>
