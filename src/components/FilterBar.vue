<template>
  <div>{{ selected }}</div>
  <div v-for="item in props.items">
    <p>{{ item.label }}</p>
    <DatePicker
      v-if="item.type === 'date'"
      v-model="selected[item.key]"
    ></DatePicker>
    <MultiSelect
      v-if="item.type === 'multiSelect'"
      v-model="selected[item.key]"
    ></MultiSelect>
    <SingleSelect
      v-if="item.type === 'singleSelect'"
      v-model="selected[item.key]"
    ></SingleSelect>
  </div>
</template>
<script setup>
import DatePicker from './DatePicker.vue';
import MultiSelect from './MultiSelect.vue';
import SingleSelect from './SingleSelect.vue';
import { reactive } from 'vue';

const selected = reactive({});

const props = defineProps({
  items: {
    type: Array,
    required: true,
    validator(val) {
      let isValidObj = val.every(
        (obj) =>
          obj.hasOwnProperty('type') &&
          obj.hasOwnProperty('label') &&
          obj.hasOwnProperty('key')
      );
      if (!isValidObj) {
        console.warn('The object should have username and email');
        return false;
      }
      return true;
    },
  },
});
</script>
