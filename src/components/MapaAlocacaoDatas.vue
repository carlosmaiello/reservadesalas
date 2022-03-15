<template>
    <div class="mapa-alocacao-sala-dia" v-for="dia in dias" :key="dia">
      {{ dia.getDate() }}<br>
      {{ diaSemana(dia) }}
    </div>
</template>

<script>
const weekday = ["D","S","T","Q","Q","S","S"];
export default {
props: ["inicio", "fim"],
  computed: {
    dias() {
      let dias = [];
      for (let d = new Date(Number(this.inicio)); d <= this.fim; d.setDate(d.getDate() + 1)) {
        dias.push(new Date(Number(d)));
      }

      return dias;
    },
  },
  methods: {
      diaSemana(dia) {
          return weekday[dia.getDay()];
      }
  }
}
</script>

<style>

</style>