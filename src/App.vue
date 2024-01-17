<script lang="ts">
  import { withModifiers } from "vue";
  export default {
    data () {
      return {
        withModifiers: withModifiers,
        selected: [],
        headers: [
          {
            title: "Name",
            key: "name",
          },
          {
            title: "Location",
            key: "location",
          },
          {
            title: "Height",
            key: "height",
          },
          {
            title: "Base",
            key: "base",
          },
          {
            key: "data-table-select",
          },
          {
            title: "Volume",
            key: "volume",
          },
        ],
        items: [
          {
            name: '🍎 Apple',
            location: 'Washington',
            height: '0.1',
            base: '0.07',
            volume: '0.0001',
          },
          {
            name: '🍌 Banana',
            location: 'Ecuador',
            height: '0.2',
            base: '0.05',
            volume: '0.0002',
          },
          {
            name: '🍇 Grapes',
            location: 'Italy',
            height: '0.02',
            base: '0.02',
            volume: '0.00001',
          },
          {
            name: '🍉 Watermelon',
            location: 'China',
            height: '0.4',
            base: '0.3',
            volume: '0.03',
          },
          {
            name: '🍍 Pineapple',
            location: 'Thailand',
            height: '0.3',
            base: '0.2',
            volume: '0.005',
          },
          {
            name: '🍒 Cherries',
            location: 'Turkey',
            height: '0.02',
            base: '0.02',
            volume: '0.00001',
          },
          {
            name: '🥭 Mango',
            location: 'India',
            height: '0.15',
            base: '0.1',
            volume: '0.0005',
          },
          {
            name: '🍓 Strawberry',
            location: 'USA',
            height: '0.03',
            base: '0.03',
            volume: '0.00002',
          },
          {
            name: '🍑 Peach',
            location: 'China',
            height: '0.09',
            base: '0.08',
            volume: '0.0004',
          },
          {
            name: '🥝 Kiwi',
            location: 'New Zealand',
            height: '0.05',
            base: '0.05',
            volume: '0.0001',
          },
        ],
      }
    },
  }
</script>

<template>
  <v-app>
    <v-data-table
      v-model="selected"
      :headers="headers"
      :items="items"
      item-value="name"
    >
      <template v-slot:[`header.data-table-select`]="{ someSelected, allSelected, selectAll }">
        <v-checkbox-btn
          :modelValue="allSelected"
          :indeterminate="someSelected && !allSelected"
          @update:model-value="selectAll"
          color="primary"
          class="indeterminate-checkbox"
        />
      </template>
      <template v-slot:[`item.data-table-select`]="{ isSelected, toggleSelect, internalItem }">
        <v-checkbox-btn
          :modelValue="isSelected([internalItem])"
          :onclick="withModifiers(() => toggleSelect(internalItem), ['stop'])"
          color="primary"
        />
      </template>
    </v-data-table>
  </v-app>
</template>

<style scoped>
/* 部分選択時のマイナスアイコンを青くする */
.indeterminate-checkbox.v-checkbox-btn :deep(.v-selection-control__input) > .v-icon.mdi-minus-box {
  color: #1867c0;
  opacity: 1;
}
</style>
