<template>
  <div>
    <form>
      <label for="income">Enter Monthly Income from Various Sources:</label>
      <input v-model="income" @keyup.enter="sumIncome" type="text" name="income" />
      <button @click.prevent="sumIncome">Get Total</button>
    </form>
    <p>Total Monthly Income: {{ totalMonthlyIncome }}</p>
  </div>
</template>

<script>
import { mapState } from 'vuex';

export default {
  data() {
    return {
      income: '',
    };
  },
  computed: mapState(['totalMonthlyIncome']),
  methods: {
    sumIncome() {
      this.$store.commit('TOTAL_MONTHLY_INCOME', this.income);
      this.income = '';
    },
  },
};
</script>

<style lang="scss" scoped>
div {
  display: flex;
  flex-flow: column nowrap;
  justify-content: flex-start;
  padding: 0.5em;
}
</style>
