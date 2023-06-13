<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div class="movement">{{ title }}</div>
</template>

<script setup>
import { defineProps, toRefs } from "vue";

const props = defineProps({
  title: {
    type: String,
    default: "",
    required: true,
  },
});

const { title } = toRefs(props);
</script>
