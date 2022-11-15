<template>
  <VueMultiselect
    v-model="selected"
    @update:model-value="updateSelected"
    :options="singleSelectOptions"
    label="name"
    track-by="value"
  >
  </VueMultiselect>
</template>
<script setup>
import { ref } from 'vue';
import 'vue-multiselect/dist/vue-multiselect.css';
import VueMultiselect from 'vue-multiselect';
const emit = defineEmits(['update:modelValue']);
let selectedMultiSelect;
const singleSelectOptions = ref([]);

singleSelectOptions.value = props?.options?.map((o) => {
  const option = {};
  option.name = o[props.nameKey];
  option.value = o[props.valueKey];
  return option;
});
console.log({ singleSelectOptions: singleSelectOptions.value });
const props = defineProps({
  modelValue: String,
  nameKey: String,
  valueKey: String,
  options: {
    type: Array,
    required: true,
  },
});
let selected = ref();
const updateSelected = (newValue) => {
  selected.value = newValue;
  emit('update:modelValue', newValue);
};
</script>
