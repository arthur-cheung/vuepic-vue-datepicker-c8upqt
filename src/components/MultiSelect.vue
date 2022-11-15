<template>
  <VueMultiselect
    v-if="props.grouped"
    v-model="selected"
    @update:model-value="updateSelected"
    :options="multiSelectOptions"
    :multiple="true"
    label="name"
    track-by="value"
    :group-select="props.grouped"
    group-label="groupLabel"
    group-values="groupValues"
  >
  </VueMultiselect>
  <VueMultiselect
    v-if="!props.grouped"
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
  grouped: Boolean,
  groupField: String,
});
const multiSelectOptions = ref([]);

console.log({ grouped: props.grouped, groupField: props.groupField });

if (!props.grouped) {
  multiSelectOptions.value = props?.options?.map((o) => {
    const option = {};

    option.name = o[props.nameKey];
    option.value = o[props.valueKey];

    return option;
  });
} else {
  const groups = [...new Set(props?.options?.map((o) => o[props?.groupField]))];
  multiSelectOptions.value = groups.map((g) => {
    const option = {};
    option.groupLabel = g;
    option.groupValues = props?.options?.filter(
      (o) => o[props?.groupField] === g
    );
    return option;
  });
}
let selected = ref();
const updateSelected = (newValue) => {
  selected.value = newValue;
  emit('update:modelValue', newValue);
};
</script>
