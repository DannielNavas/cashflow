<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <Layaout>
    <template #header>
      <Header></Header>
    </template>
    <template #resume>
      <Resume :label="title" :amount="amount" :total-amount="totalAmount">
        <template #graphic>
          <Graphic :amounts="amounts" @select="select" />
        </template>
        <template #action>
          <Action @create="create" />
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movements :movements="movements" @remove="remove" />
    </template>
  </Layaout>
</template>

<script>
import Header from "@/components/Header.vue";
import Layaout from "@/components/Layout.vue";
import Action from "./Action.vue";
import Movements from "./Movements/Index.vue";
import Graphic from "./Resume/Graphic.vue";
import Resume from "./Resume/Index.vue";

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Home",
  components: {
    Layaout,
    Header,
    Resume,
    Movements,
    Action,
    Graphic,
  },
  data() {
    return {
      amount: 0,
      movements: [],
    };
  },
  computed: {
    title() {
      return this.amount > 0 ? "Disponible" : "Ahoro total";
    },
    amounts() {
      const lastDays = this.movements
        .filter((m) => {
          const today = new Date();
          const oldDate = today.setDate(today.getDate() - 30);

          return m.time.getTime() > oldDate;
        })
        .map((m) => m.amount);

      return lastDays.map((m, i) => {
        const lastMovements = lastDays.slice(0, i + 1);

        return lastMovements.reduce((a, b) => a + b, 0);
      });
    },
    totalAmount() {
      return this.movements.reduce(
        (sumaTotal, movimiento) => sumaTotal + movimiento.amount,
        0
      );
    },
  },
  mounted() {
    const movements = JSON.parse(localStorage.getItem("movements")) || [];
    this.movements = movements?.map((m) => {
      return { ...m, time: new Date(m.time) };
    });
  },
  methods: {
    create(movement) {
      this.movements.push(movement);
      this.save();
    },
    remove(id) {
      const index = this.movements.findIndex((m) => m.id === id);
      this.movements.splice(index, 1);
      this.save();
    },
    save() {
      localStorage.setItem("movements", JSON.stringify(this.movements));
    },
    select(amount) {
      this.amount = amount;
    },
  },
};
</script>
