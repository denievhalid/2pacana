<template>
  <div class="wrapper">
    <div class="containers">
      <div class="containers__top">
        <v-own-items :selected="selectedOwnItems" />
        <v-general-item :item="selectedGeneralItem" />
      </div>
      <div class="containers__bottom">
        <v-items
          big
          :selected="selectedOwnItems"
          :items="ownItems"
          :type="TYPES.OWN"
          @select="selectItem"
        />
        <v-items
          big
          :selected="selectedOwnItems"
          :type="TYPES.GENERAL"
          :items="items"
          @select="selectItem"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import VItems from "./components/v-items";
import VOwnItems from "./components/v-own-items";
import VGeneralItem from "./components/v-general-item";
import { TYPES } from "./constants";
import { find } from "lodash";
import data from "./data";

const items = ref(data.items);
const ownItems = ref(data.ownItems);

const selectedOwnItems = ref([]);
const selectedGeneralItem = ref(null);

const selectItem = (item, type) => {
  switch (type) {
    case TYPES.OWN:
      if (find(selectedOwnItems.value, { id: item.id })) {
        selectedOwnItems.value = selectedOwnItems.value.filter(
          (s) => s.id !== item.id
        );
      } else if (selectedOwnItems.value.length < 6) {
        selectedOwnItems.value.push(item);
      }

      break;

    case TYPES.GENERAL:
      selectedGeneralItem.value = item;
  }
};
</script>

<style></style>
