<template>
  <div class="mapa-alocacao">
    <div class="mapa-alocacao-topo"></div>
    <div class="mapa-alocacao-salas">
      <MapaAlocacaoSala :sala="sala" v-for="sala in salas" :key="sala.id" :inicio="inicio" :fim="fim" />
    </div>
  </div>
</template>

<script>
import MapaAlocacaoSala from "./MapaAlocacaoSala.vue";
export default {
  props: ["predio", "periodo", "salas"],
  components: { MapaAlocacaoSala },
  data() {
    return {
      inicio: new Date(2022, 2, 1),
      fim: new Date(2022, 2, 31),
    };
  },
};
</script>

<style>
.mapa-alocacao-sala { display: flex; }
.mapa-alocacao-sala-nome { width: 200px; }
.mapa-alocacao-sala-dia { width: 30px; }
.mapa-alocacao-reserva { display: block; width: 20px; height: 20px; background: red; border-radius: 50%; font-size: 0!important;}
</style>