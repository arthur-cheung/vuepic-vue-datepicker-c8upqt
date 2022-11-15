<script setup>
import FilterBar from './components/FilterBar.vue';
const items = [
  {
    label: 'Date',
    type: 'date',
    key: 'date',
  },
  {
    label: 'Another Date',
    type: 'date',
    key: 'date2',
  },
  {
    label: 'Multi Select',
    type: 'multiSelect',
    key: 'multiSelect',
    nameKey: 'name',
    valueKey: 'id',
    options: [
      { name: 'A', id: 1 },
      { name: 'B', id: 2 },
      { name: 'C', id: 3 },
      { name: 'D', id: 4 },
      { name: 'E', id: 5 },
    ],
  },
   {
    label: 'Kelly\'s special Field',
    type: 'multiSelect',
    key: 'kelly',
    nameKey: 'name',
    valueKey: 'id',
    options: [
      { name: 'Kelly', id: 1 },
      { name: 'Arthur', id: 2 },
      { name: 'Brayden', id: 3 },
      { name: 'D', id: 4 },
      { name: 'E', id: 5 },
    ],
  },
  {
    label: 'Single Select',
    type: 'singleSelect',
    key: 'singleSelect',
    nameKey: 'userName',
    valueKey: 'id',
    options: [
      { userName: 'user A', id: 'a' },
      { userName: 'user B', id: 'b' },
      { userName: 'user C', id: 'c' },
      { userName: 'user D', id: 'd' },
      { userName: 'user E', id: 'e' },
    ],
  },
];
</script>

<template>
  <FilterBar :items="items" />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
