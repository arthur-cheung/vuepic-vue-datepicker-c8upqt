<template>
  <VueMultiselect
    v-model="selected"
    @update:model-value="updateSelected"
    :options="singleSelectOptions"
    label="name"
    track-by="name"
  >
  </VueMultiselect>
</template>
<script setup>
import { ref } from 'vue';
import 'vue-multiselect/dist/vue-multiselect.css';
import VueMultiselect from 'vue-multiselect';
const emit = defineEmits(['update:modelValue']);
let selectedMultiSelect;
const singleSelectOptions = [
  { name: 'one', value: 1 },
  { name: 'two', value: 2 },
  { name: 'three', value: 3 },
  { name: 'four', value: 4 },
];
const props = defineProps({
  modelValue: String,
});
let selected = ref();
const updateSelected = (newValue) => {
  selected.value = newValue;
  emit('update:modelValue', newValue);
};
</script>
