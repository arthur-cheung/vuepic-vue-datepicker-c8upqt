<template>
  <VueMultiselect
    v-model="selected"
    @update:model-value="updateSelected"
    :options="multiSelectOptions"
    :multiple="true"
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
const props = defineProps({
  modelValue: String,
  nameKey: String,
  valueKey: String,
  options: {
    type: Array,
    required: true,
  },
});
const multiSelectOptions = ref([]);

multiSelectOptions.value = props?.options?.map((o) => {
  const option = {};
  option.name = o[props.nameKey];
  option.value = o[props.valueKey];
  return option;
});
let selected = ref();
const updateSelected = (newValue) => {
  selected.value = newValue;
  emit('update:modelValue', newValue);
};
</script>
