<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <Layaout>
    <template #header>
      <Header></Header>
    </template>
    <template #resume>
      <Resume :label="title" :amount="amount" :total-amount="10000000">
        <template #graphic>
          <!-- <img src="@/assets/Graphic.svg" alt="Graphic" /> -->
          Grafica
        </template>
        <template #action>
          <button class="button">Ver todos</button>
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movements :movements="movements" />
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
  data() {
    return {
      amount: 0,
      movements: [
        {
          id: 1,
          title: "Movimiento",
          description: "Deposito de salario",
          amount: "1000",
        },
        {
          id: 2,
          title: "Movimiento 1",
          description: "Deposito de honorarios",
          amount: "500",
        },
        {
          id: 3,
          title: "Movimiento 3",
          description: "Comida",
          amount: "-100",
        },
        {
          id: 4,
          title: "Movimiento 4",
          description: "Colegiatura",
          amount: "1000",
        },
        {
          id: 5,
          title: "Movimiento 5",
          description: "Reparación equipo",
          amount: "1000",
        },
      ],
    };
  },
  computed: {
    title() {
      return this.amount > 0 ? "Disponible" : "Ahoro total";
    },
  },
};
</script>
