<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <Layaout>
    <template #header>
      <Header></Header>
    </template>
    <template #resume>
      <Resume></Resume>
    </template>
    <template #movements>
      <Movements></Movements>
    </template>
  </Layaout>
</template>

<script>
import Header from "@/components/Header.vue";
import Layaout from "@/components/Layout.vue";
import Movements from "./Movements/Index.vue";
import Resume from "./Resume/Index.vue";

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Home",
  components: {
    Layaout,
    Header,
    Resume,
    Movements,
  },
};
</script>
