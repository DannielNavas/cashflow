<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <Layaout>
    <template #header>
      <Header></Header>
    </template>
  </Layaout>
</template>

<script>
import Layaout from "@/components/Layout.vue";
import Header from "@/components/Header.vue";

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Home",
  components: {
    Layaout,
    Header,
  },
};
</script>
