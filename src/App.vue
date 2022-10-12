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

const items = ref([
  {
    id: 11,
    name: "Jacket 1",
  },
  {
    id: 12,
    name: "Jacket 2",
  },
  {
    id: 13,
    name: "Jacket 3",
  },
  {
    id: 14,
    name: "Jacket 4",
  },
  {
    id: 15,
    name: "Hoodie 1",
  },
  {
    id: 16,
    name: "Hoodie 2",
  },
  {
    id: 17,
    name: "Hoodie 3",
  },
  {
    id: 18,
    name: "Hoodie 4",
  },
]);

const ownItems = ref([
  {
    id: 1,
    name: "Shoes 1",
  },
  {
    id: 2,
    name: "Shoes 2",
  },
  {
    id: 3,
    name: "Shoes 3",
  },
  {
    id: 4,
    name: "Shoes 4",
  },
  {
    id: 5,
    name: "T-shirt 1",
  },
  {
    id: 6,
    name: "T-shirt 2",
  },
  {
    id: 7,
    name: "T-shirt 3",
  },
  {
    id: 8,
    name: "T-shirt 4",
  },
]);

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
