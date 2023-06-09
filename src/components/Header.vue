<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <header>
    <img
      src="@/assets/cashflow-icon_070076db-e83a-4afa-b18d-ee058c2b646e.svg"
      alt="Logo"
      @click="reload"
    />
    <h1><span>Cahs</span>Flow</h1>
    <span></span>
  </header>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Header",
  methods: {
    reload() {
      window.location.reload();
    },
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-around;
  align-items: center;
  width: 100vw;
}
img,
span {
  width: 48px;
}
h1 {
  font-size: 1.4rem;
  color: var(--brand-blue);
}
h1 span {
  color: var(--brand-green);
}
</style>
