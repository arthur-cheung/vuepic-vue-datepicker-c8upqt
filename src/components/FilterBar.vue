<template>
  <div v-if="props.date">
    <DatePicker v-model="selectedDate"></DatePicker>
    <p>{{ selectedDate }}</p>
  </div>
  <div>
    <MultiSelect v-model="selectedMultiSelectValue"></MultiSelect>
    <p>{{ selectedMultiSelectValue }}</p>
  </div>
</template>
<script setup>
import DatePicker from './DatePicker.vue';
import MultiSelect from './MultiSelect.vue';
import { ref } from 'vue';

const props = defineProps({
  date: Boolean,
});

const selectedDate = ref();
const selectedMultiSelectValue = ref();
</script>
