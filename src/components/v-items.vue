<template>
  <div class="items" :class="{ 'items--big': big }">
    <div
      class="item"
      :class="{ 'item--active': isActive(item) }"
      v-for="item in items"
      :key="item.id"
      @click="selectHandler($event, item)"
    >
      {{ item.name }}
    </div>
  </div>
</template>

<script setup>
import { find } from "lodash";

const emit = defineEmits(["select"]);

const props = defineProps({
  active: Boolean,
  big: Boolean,
  type: String,
  items: Array,
  selected: Array,
});

const selectHandler = (e, item) => {
  emit("select", item, props.type);
};

const isActive = (item) => {
  return find(props.selected, { id: item.id });
};
</script>

<style scoped>
.items {
  background-color: #f2f3f5;
  padding: 20px;
  border-radius: 6px;
  display: grid;
  gap: 20px;
  width: 220px;
  grid-template-columns: repeat(2, 1fr);
}
.item {
  background-color: #fff;
  width: 80px;
  height: 80px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
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
