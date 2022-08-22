<script>
export default {
  data() {
    return {
      qualidades: [
        { qualidade: 5, servico: "5% (Péssimo)" },
        { qualidade: 10, servico: "10% (Ruim)" },
        { qualidade: 15, servico: "15% (OK)" },
        { qualidade: 20, servico: "20% (Bom)" },
        { qualidade: 25, servico: "25% (Mais que bom)" },
        { qualidade: 30, servico: "30% (Excelente)" },
      ],
      valor: 0,
      pessoa: 1,
      qualidade_selecionada: "",
    };
  },
  computed: {
    valor_final() {
      return (
        (this.valor * (1 + this.qualidade_selecionada / 100)) /
        this.pessoa
      ).toFixed(2);
    },
  },
};
</script>

<template>
  <main>
    <div class="froms-gorjeta">
      <h1>Calculadora de Gorjetas</h1>
      <div class="forms-gorjeta-value">
        <label for="">Qual o valor da conta?</label>
        <input type="number" v-model="valor" placeholder="0" />
      </div>
      <div class="forms-gorjeta-value">
        <label for="select-servico">Como foi o serviço?</label>
        <select
          name="select-qualidade "
          id="select-servico"
          v-model="qualidade_selecionada"
        >
          <option disabled>Escolha um item</option>
          <option
            v-for="qualidade of qualidades"
            :key="qualidade.qualidade"
            for="select-servico"
            :value="qualidade.qualidade"
          >
            {{ qualidade.servico }}
          </option>
        </select>
      </div>

      <div class="forms-gorjeta-value">
        <label for="">Quantas pessoas irão pagar?</label>
        <input type="number" v-model="pessoa" placeholder="1" />
      </div>

      <div class="resultado">
        <h3>Valor da conta:</h3>
        <span>R$ {{ valor_final }} por pessoa</span>
      </div>
    </div>
  </main>
</template>
