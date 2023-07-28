<template>
  <li
    class="list-group-item d-flex justify-content-between align-items-center"
    :class="[{ like: movie.like }, { fovorite: movie.fovorite }]"
  >
    <span
      class="list-group-item-text"
      @click="$emit('onToggle', { id: movie.id, prop: 'like' })"
      >{{ movie.name }}</span
    >
    <input type="nummber" class="list-group-item-input" :value="movie.viwers" />
    <div class="d-flex justify-content-center align-items-center">
      <button
        type="button"
        class="btn-cookie"
        @click="$emit('onToggle', { id: movie.id, prop: ' fovorite' })"
      >
        <i class="fas fa-cookie"></i>
      </button>
      <button
        type="button"
        class="btn-trash"
        @click="$emit('onRemove', movie.id)"
      >
        <i class="fas fa-trash text-danger"></i>
      </button>
      <i class="fas fa-star text-warning"></i>
    </div>
  </li>
</template>

<script>
export default {
  props: {
    movie: {
      type: Object,
      reqiured: true,
    },
  },
  methods: {},
};
</script>

<style scoped>
.list-group-item {
  padding: 15px 20px;
  border: none;
  border-bottom: 1px solid #3d5a80;
  transition: all 0.3s linear;
}
.list-group-item:hover {
  border-bottom: 1px solid #f5a83b;
}
.list-group-item:last-child {
  border-bottom: none;
}
.list-group-item span {
  line-height: 35px;
  font-size: 20px;
  cursor: pointer;
  width: 550px;
}
.list-group-item input {
  line-height: 35px;
  font-size: 20px;
  text-align: center;
  border: 0;
  outline: none;
}
.list-group-item button {
  width: 35px;
  height: 35px;
  margin: 3px;
  font-size: 17px;
  border: none;
  cursor: pointer;
  border-radius: 5px;
}
.list-group-item .btn-cookie {
  color: #f5a83b;
}
.list-group-item .fa-star {
  transform: translateX(30px);
  transition: all 0.3s ease;
  opacity: 0;
}
.list-group-item.like .fa-star {
  transform: translateX(0);
  opacity: 1;
}
.list-group-item.fovorite .list-group-item-text,
list-group-item.fovorite .list-group-item-input {
  color: #f5a83b;
}
</style>
