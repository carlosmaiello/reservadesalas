<template>
  <div class="container">
    <ul class="nav nav-pills fs-3 my-2">
      <li class="nav-item" v-for="predio in predios" :key="predio.id">
        <a
          :class="{
            'nav-link': true,
            active: predioSelecionado && predioSelecionado.id == predio.id,
          }"
          aria-current="page"
          href="#"
          @click.prevent="predioSelecionado = predio"
          >{{ predio.nome }}</a
        >
      </li>
    </ul>

    <ul class="nav nav-pills fs-5 my-2">
      <li class="nav-item" v-for="periodo in periodos" :key="periodo.id">
        <a
          :class="{
            'nav-link': true,
            active: periodoSelecionado && periodoSelecionado.id == periodo.id,
          }"
          aria-current="page"
          href="#"
          @click.prevent="periodoSelecionado = periodo"
          >{{ periodo.nome }}</a
        >
      </li>
    </ul>

    <MapaAlocacao :predio="predioSelecionado" :periodo="periodoSelecionado" :salas="salas" />
  </div>
</template>

<script>
import MapaAlocacao from "../components/MapaAlocacao.vue";
export default {
    data() {
        return {
            predios: [
                {
                    id: 1,
                    nome: "BAU1",
                },
                {
                    id: 2,
                    nome: "BAU2",
                },
            ],
            predioSelecionado: null,
            periodos: [
                {
                    id: 1,
                    nome: "Manhã",
                },
                {
                    id: 2,
                    nome: "Tarde",
                },
                {
                    id: 3,
                    nome: "Noite",
                },
            ],
            periodoSelecionado: null,
            salas: [
                {
                    id: 1,
                    nome: "Sala 1",
                    alocacoes: [
                        {
                            id: 1,
                            data: new Date(2022, 2, 14),
                            periodo: {
                                id: 1,
                                nome: "Manhã"
                            }
                        },
                        {
                            id: 2,
                            data: new Date(2022, 2, 17),
                            periodo: {
                                id: 1,
                                nome: "Manhã"
                            }
                        }
                    ]
                },
                {
                    id: 2,
                    nome: "Sala 2",
                },
                {
                    id: 3,
                    nome: "Sala 3",
                },
            ],
        };
    },
    components: { MapaAlocacao }
};
</script>
