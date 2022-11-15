<template>
  <Datepicker
    v-model="date"
    range
    :presetRanges="presetRanges"
    multiCalendars
    :enableTimePicker="false"
    :multiStatic="false"
    @update:modelValue="handleDate"
  >
    <template #yearly="{ label, range, presetDateRange }">
      <span @click="presetDateRange(range)">{{ label }}</span>
    </template>
  </Datepicker>
</template>

<script setup>
import { ref } from 'vue';
import Datepicker from '@vuepic/vue-datepicker';
import '@vuepic/vue-datepicker/dist/main.css';
import {
  endOfMonth,
  endOfYear,
  startOfMonth,
  startOfYear,
  startOfWeek,
  endOfWeek,
  subMonths,
  subWeeks,
  subDays,
  addDays,
  addWeeks,
  addMonths,
} from 'date-fns';

const emit = defineEmits(['update:modelValue']);
const props = defineProps({
  modelValue: [],
});
const handleDate = (modelData) => {
  emit('update:modelValue', modelData);
};

const date = ref();
const weekOptions = {
  weekStartsOn: 1,
};
const presetRanges = ref([
  { label: 'Today', range: [new Date(), new Date()] },
  {
    label: 'Tomorrow',
    range: [addDays(new Date(), 1), addDays(new Date(), 1)],
  },
  {
    label: 'Yesterday',
    range: [subDays(new Date(), 1), subDays(new Date(), 1)],
  },
  {
    label: 'This week',
    range: [
      startOfWeek(new Date(), weekOptions),
      endOfWeek(new Date(), weekOptions),
    ],
  },
  {
    label: 'Next week',
    range: [
      startOfWeek(addWeeks(new Date(), 1), weekOptions),
      endOfWeek(addWeeks(new Date(), 1), weekOptions),
    ],
  },
  {
    label: 'Last week',
    range: [
      startOfWeek(subWeeks(new Date(), 1), weekOptions),
      endOfWeek(subWeeks(new Date(), 1), weekOptions),
    ],
  },
  {
    label: 'Last 5 weeks',
    range: [
      startOfWeek(subWeeks(new Date(), 5), weekOptions),
      endOfWeek(subWeeks(new Date(), 1), weekOptions),
    ],
  },
  {
    label: 'This month',
    range: [startOfMonth(new Date()), endOfMonth(new Date())],
  },
  {
    label: 'Next month',
    range: [
      startOfMonth(addMonths(new Date(), 1)),
      endOfMonth(addMonths(new Date(), 1)),
    ],
  },
  {
    label: 'Last month',
    range: [
      startOfMonth(subMonths(new Date(), 1)),
      endOfMonth(subMonths(new Date(), 1)),
    ],
  },
]);
</script>
<style lang="scss">
.dp__preset_ranges {
  width: 10rem;
}
</style>
