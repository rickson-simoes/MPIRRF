<template>
  <div id="app">
    <h1>Média Ponderada do Imposto de Renda da Receita Federal</h1>
    <strong>1 - PORCENTAGEM A SER REMOVIDA DA TAXA TOTAL:</strong> <br/>
    Valor total da ação: <input type="number" v-model.number="num1" placeholder="1000.00"/> <br/>
    Valor líquido das operações: <input type="number" v-model.number="num2" placeholder="1500.00"/> <br/>
    Valor arredondado: <strong style='color:red'>{{valorA}} %</strong><br/>
    Valor normal: <strong>{{valorA1}} %</strong><p/>

    <strong>2 - VALOR A SER ADICIONADO NO VALOR TOTAL DA AÇÃO:</strong> <br/>
    Valor total da taxa: <input type="number" v-model.number="num3" placeholder="22.76"/> <br/>
    <small><i>taxa de liquidação, registro, emolumentos, impostos, taxa operacional... etc</i></small> <br/>
    Valor arredondado: <strong style='color:red'>{{valorB}}</strong><br/>
    Valor normal: <strong>{{valorB1}}</strong><p/>

    <strong>3 - VALOR TOTAL DA AÇÃO COM PORCENTAGEM DA TAXA:</strong> <br/>
    Val: <strong style='color:red'>{{valorC}}</strong><br/>
    Valor normal: <strong>{{valorC1}}</strong><p/>


    <strong>4 - PREÇO MÉDIO:</strong> <br/>
    Quantidade de ações: <input type="number" v-model.number="num4" placeholder="100"/> <br/>
    Val: <strong style='color:red'>{{valorD}}</strong><br/>
    Valor normal: <strong>{{valorD1}}</strong><p/>

    <p/>

    <h3>Pegar o valor correspondente do número [3] desse programa e faz o mesmo procedimento para ações de outros dias, com isso soma o valor total das ações e divide pela quantidade total de ações (Ex: 5.338,35 / 504) = preço médio = 10,59</h3>

  </div>
</template>

<script>


export default {
  name: 'mpirrf',
  data(){
    return {
      num1: '',
      num2: '',
      num3: '',
      num4: '',
    }
  },
  methods: {
    arredondador(val) {
      var numeroRecebido = Number(val)
      var arredondamento = numeroRecebido.toFixed(2);
      var numeroArredondado = Number(arredondamento);

      return numeroArredondado;
    }
  },
  computed: {
    valorA() {
      const valorRecebido = (this.num1 * 100) / this.num2;
      return this.arredondador(valorRecebido);
    },
    valorA1() {
      const valorRecebido = (this.num1 * 100) / this.num2;
      return valorRecebido;
    },

    valorB() {
      const valorRecebido = (this.valorA * this.num3) / 100;
      return this.arredondador(valorRecebido);
    },
    valorB1() {
      const valorRecebido = (this.valorA1 * this.num3) / 100;
      return valorRecebido;
    },

    valorC() {
      const valorRecebido = this.valorB + this.num1;
      return this.arredondador(valorRecebido);
    },
    valorC1() {
      const valorRecebido = this.valorB1 + this.num1;
      return valorRecebido;
    },

    valorD() {
      const valorRecebido = this.valorC / this.num4;
      return this.arredondador(valorRecebido);
    },
    valorD1() {
      const valorRecebido = this.valorC1 / this.num4;
      return valorRecebido;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
