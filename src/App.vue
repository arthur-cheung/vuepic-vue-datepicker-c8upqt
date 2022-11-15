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
  },
  {
    label: 'Single Select',
    type: 'singleSelect',
    key: 'singleSelect',
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
