<template>
  <div class="mapa-alocacao-sala">
    <div class="mapa-alocacao-sala-nome">
      {{ sala.nome }}
    </div>
    <div class="mapa-alocacao-sala-dia" v-for="dia in dias" :key="dia">
      <span class="mapa-alocacao-reserva" v-if="hasAlocacao(dia)">{{ dia.getDate() }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: ["sala", "inicio", "fim"],
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
      hasAlocacao(dia) {
          let alocacoes = [];
          if (this.sala.alocacoes)
            alocacoes = this.sala.alocacoes.filter(a => a.data.getTime() === dia.getTime());

          return alocacoes && alocacoes.length > 0;
      }
  }
};
</script>

<style>
</style>