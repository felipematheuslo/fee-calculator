<template>
  <v-container fluid>
    <v-layout>
      <v-app-bar color="indigo-darken-3" class="pa-0 ma-0">
        <v-btn
          size="large"
          icon="mdi-home"
          class="ma-0"
          href="index.html"
        >
        </v-btn>
        <v-app-bar-title class="flex text-center ml-0 mr-14">
          <p class="webPageName"> Calcula pra mim! </p>
        </v-app-bar-title>
      </v-app-bar>

      <v-main>
      <v-row justify="center" class="py-0 mt-3">
          <v-col align="center" class="py-0 mb-3">
            <v-text class="text-wrap text-h5">
              Expectativas de mercado
            </v-text>
          </v-col>
        </v-row>

        <v-row justify="center" class="py-0 mb-10">
          <v-col cols="12" md="8" align="center" class="py-0">
            <v-text class="mb-2 text-wrap">
              Resumo das projeções dos principais índices de mercado para os próximos anos.
            </v-text>
          </v-col>
        </v-row>

        <v-row justify="center" class="mt-3 mb-10">
          <v-col cols="12" md="8" align="center" class="pa-0">
            <v-card
              color="indigo-darken-1"
              variant="outlined"
              class="mx-2 py-1"
            >
              <v-data-table
                :headers="headers"
                :items="projecoes"
                items-per-page="-1"
              >
              </v-data-table>

              <v-card-text class="pb-0">
                Fonte: 
                
                <a href="https://www.bcb.gov.br/publicacoes/focus" target="_blank" rel="noopener noreferrer">
                Relatório Focus - Banco Central do Brasil
                </a>
              </v-card-text>

              <v-card-subtitle>
                Atualizado em: {{updateDate}}
              </v-card-subtitle>
            </v-card>
          </v-col>
        </v-row>

        <v-row justify="center" class="my-5">
          <v-col cols="12" md="8" align="center" class="py-0">
            <v-text class="text-wrap">
              <p class="text-h6">
              O que é o Relatório Focus?
              </p>

              <br/>
            
              <p class="text-justify">
                O Relatório Focus é um boletim semanal divulgado pelo Banco Central do Brasil que apresenta projeções econômicas de diversos indicadores, como inflação, taxa de juros, crescimento do Produto Interno Bruto (PIB) e taxa de câmbio. Essas projeções são feitas por instituições financeiras e consultorias econômicas que participam da pesquisa. O objetivo do Relatório Focus é fornecer informações relevantes para auxiliar na análise e no acompanhamento da economia brasileira, sendo uma ferramenta importante para investidores, empresas e formuladores de políticas públicas.
              </p>
            </v-text>
          </v-col>
        </v-row>
      </v-main>
    </v-layout>
  </v-container>
</template>

<script>
import focus from '../assets/focus.json'

export default {
  data () {
    return {
      focus: focus,

      updateDate: '',
      headers: [
        { title: 'Índice', align: 'center', key: 'indice', sortable: false },
        { title: focus.ano0, align: 'center', key: 'ano0', sortable: false },
        { title: focus.ano1, align: 'center', key: 'ano1', sortable: false },
        { title: focus.ano2, align: 'center', key: 'ano2', sortable: false },
        { title: focus.ano3, align: 'center', key: 'ano3', sortable: false },
      ],
      projecoes: [
        {
          indice: 'IPCA (variação%)',
          ano0: focus.ipca[0].ano0,
          ano1: focus.ipca[0].ano1,
          ano2: focus.ipca[0].ano2,
          ano3: focus.ipca[0].ano3,
        },
        {
          indice: 'Selic (% a.a)',
          ano0: focus.selic[0].ano0,
          ano1: focus.selic[0].ano1,
          ano2: focus.selic[0].ano2,
          ano3: focus.selic[0].ano3,
        },
        {
          indice: 'Dólar (R$/US$)',
          ano0: focus.dolar[0].ano0,
          ano1: focus.dolar[0].ano1,
          ano2: focus.dolar[0].ano2,
          ano3: focus.dolar[0].ano3,
        },
        {
          indice: 'IGP-M (variação%)',
          ano0: focus.igpm[0].ano0,
          ano1: focus.igpm[0].ano1,
          ano2: focus.igpm[0].ano2,
          ano3: focus.igpm[0].ano3,
        },
      ],
    }
  },
  mounted () {
    this.updateDate = this.focus.updateDate
  },
  methods: {
  },
};
</script>

<style>
.webPageName {
  font-family: 'Brush Script MT', cursive;
  font-size: 30px
}
.v-data-table-header__content {
  font-weight: bolder;
}
.v-data-table-footer {
  display: none !important;
}
</style>