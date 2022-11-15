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
      :name-key="item.nameKey"
      :value-key="item.valueKey"
      :options="item.options"
      :grouped="!!item.grouped"
      :group-field="item.groupField"
    ></MultiSelect>
    <SingleSelect
      v-if="item.type === 'singleSelect'"
      :name-key="item.nameKey"
      :value-key="item.valueKey"
      v-model="selected[item.key]"
      :options="item.options"
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
        console.warn('The object requires a type, label and key');
        return false;
      }
      return true;
    },
  },
});
</script>
