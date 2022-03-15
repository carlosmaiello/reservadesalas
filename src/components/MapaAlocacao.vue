<template>
  <div class="mapa-alocacao">
    <div class="mapa-alocacao-topo">
      <MapaAlocacaoDatas :inicio="inicio" :fim="fim" />
    </div>
    <div class="mapa-alocacao-salas">
      <MapaAlocacaoSala :sala="sala" v-for="sala in salas" :key="sala.id" :inicio="inicio" :fim="fim" />
    </div>
  </div>
</template>

<script>
import MapaAlocacaoSala from "./MapaAlocacaoSala.vue";
import MapaAlocacaoDatas from "./MapaAlocacaoDatas.vue";
export default {
  props: ["predio", "periodo", "salas"],
  components: { MapaAlocacaoSala, MapaAlocacaoDatas },
  data() {
    return {
      inicio: new Date(2022, 2, 1),
      fim: new Date(2022, 2, 31),
    };
  },
};
</script>

<style>
.mapa-alocacao { overflow-x: auto; }
.mapa-alocacao-sala { display: flex; }
.mapa-alocacao-sala-nome { width: 200px; flex: 0 0 200px; }
.mapa-alocacao-topo { padding-left: 200px; display: flex; }
.mapa-alocacao-sala-dia { width: 40px; text-align: center; flex: 0 0 40px;}
.mapa-alocacao-reserva { display: inline-block; width: 20px; height: 20px; background: red; border-radius: 50%; font-size: 0!important;}
</style>