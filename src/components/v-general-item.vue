<template>
  <div class="items">
    <div class="item" v-if="item">
      {{ item.name }}
    </div>
  </div>
</template>

<script setup>
const emit = defineEmits(["select"]);

const props = defineProps({
  item: Object,
});
</script>

<style scoped>
.items {
  background-color: #f2f3f5;
  padding: 20px;
  border-radius: 6px;
  display: grid;
  width: 220px;
}
.item {
  background-color: #fff;
  width: 180px;
  height: 180px;
  cursor: pointer;
  border-radius: 6px;
  transition: transform 0.1s ease-in-out;
}
.item--active {
  background-color: #033ddd;
  color: #fff;
}
.items--big {
  width: 420px;
  grid-template-columns: repeat(4, 1fr);
}
.item:hover {
  transform: scale(1.1);
}
</style>
