<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <main>
    <p>{{ label }}</p>
    <h1>{{ amountCurrency }}</h1>
    <div class="graphic">
      <slot name="graphic"></slot>
    </div>
    <div class="action">
      <slot name="action"></slot>
    </div>
  </main>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Resume",
  props: {
    label: {
      type: String,
      required: true,
    },
    totalAmount: {
      type: Number,
      required: true,
    },
    amount: {
      type: Number,
      required: false,
      defauld: null,
    },
  },
  computed: {
    amountVisual() {
      return this.amount > 0 ? this.amount : this.totalAmount;
    },
    amountCurrency() {
      return new Intl.NumberFormat("es-CO", {
        style: "currency",
        currency: "COP",
      }).format(this.amountVisual);
    },
  },
};
</script>

<style scoped>
main {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
}

h1,
p {
  margin: 0;
  text-align: center;
}

h1 {
  margin-top: 14px;
  color: var(--brand-green);
}

.graphic {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  padding: 48px 24px;
  box-sizing: border-box;
}
</style>
