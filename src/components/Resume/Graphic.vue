<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div>
    <svg viewBox="0 0 300 200">
      <line
        stroke="#c4c4c4"
        stroke-width="2"
        x1="0"
        y1="100"
        x2="300"
        y2="100"
      />
      <polyline
        fill="none"
        stroke="#0689B0"
        stroke-witdh="2"
        :points="points"
      />
      <line
        stroke="#04b500"
        stroke-witdh="2"
        x1="200"
        y1="0"
        x2="200"
        y2="200"
      />
    </svg>
    <p>Ultimos 30 días</p>
  </div>
</template>

<script setup>
import { computed, defineProps, toRefs } from "vue";

const props = defineProps({
  amounts: {
    type: Array,
    required: true,
    default: () => [],
  },
});

const { amounts } = toRefs(props);
const amountToPixels = (amount) => {
  const max = Math.max(...amounts.value);
  const min = Math.min(...amounts.value);
  const range = max - min;
  return ((amount - min) * 100) / range;
};

const points = computed(() => {
  const total = amounts.value.length;
  return Array(total)
    .fill(100)
    .reduce((points, amount, i) => {
      const x = (300 / total) * (i + 1);
      const y = amountToPixels(amount);
      return `${points} ${x},${y}`;
    }, "0, 100");
});
</script>

<style scoped>
svg {
  width: 100%;
}

p {
  text-align: center;
}
</style>
