<template>
  <div class="container">
    <v-items :items="selected" />
    <div class="info">Выбрано: {{ selected.size }} / 6</div>
  </div>
</template>

<script setup>
import VItems from "./v-items";

defineProps({
  selected: Map,
});
</script>

<style scoped>
.info {
  margin-top: 15px;
}
</style>
