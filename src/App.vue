<template>
  <div id="app">
     
    <section class="dashboard">
      <header>
        <h1>BAM dashboard</h1>
      </header>
       <div class="dashboard__summary">
        <total-sales-spark  :val="info" :textTit="tit" :typee="op1" />
        <total-sales-spark :val="info2" :textTit="tit2" :typee="op2"  />
        <total-sales-spark  :val="info3" :textTit="tit3" :typee="op3" />
        </div>
         <header>
      </header>
        <h2>Clientes</h2>
          <div class="dashboard__row">
        <type-of-clients-chart style="flex:2" :data="transactions"  />
        <expense-of-clients-chart :entries="transactions" />
      </div>
      <header>
      </header>
        <h2>Categorias</h2>
      <div class="dashboard__row">
          <type-of-categories-chart style="flex:2" :data="transactions"  />
         
      </div>
      <div class="dashboard__row">
         <type-of-categories-tr-chart style="flex:2" :data="transactions"  />
      </div>

    </section>
  </div>
</template>
<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 2rem;
  --light-blue: #2196f3;
}
h1 {
  margin: 0;
}
header {
  display: flex;
  justify-content: space-between;
  border-bottom: 1px solid #ddd;
  padding-bottom: 1rem;
}
nav {
  display: flex;
  align-items: center;
}
a {
  color: var(--light-blue);
  text-decoration: none;
  font-size: 1.1rem;
}
a + a {
  margin: 0 1rem;
}
a:visited {
  color: var(--light-blue);
}
a:hover {
  text-decoration: none;
}
a.router-link-exact-active {
  font-weight: 500;
  border-bottom: 2px solid var(--light-blue);
}
/* LAYOUT */
.dashboard {
  width: 100%;
}
.dashboard__summary{
  display: flex;
  justify-content: space-around;
  margin: 0.5rem 0;
}
.content {
  display: flex;
  height: 600px;
  width: 100%;
  flex-wrap: wrap;
  justify-content: center;
}
.content__col {
  display: flex;
  flex: 1;
  flex-direction: column;
  min-width: 780px;
  max-width: 780px;
  min-height: 600px;
  max-height: 600px;
}
.content__col + .content__col {
  padding-left: 1rem;
  border-left: 1px solid #ddd;
}
.content__row {
  flex: 1;
  display: flex;
}
.cell {
  flex: 1;
  margin: 1rem;
}

/* SCORECARD */
.scorecard {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 1rem;
}
.scorecard__value {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--light-blue);;
}
.scorecard__header {
  margin-top: 0.4rem;
}
.scorecard__subheader {
  font-size: 0.8rem;
}

/* CHEVRONS */
.chevron::before {
	border-style: solid;
	border-width: 0.15em 0.15em 0 0;
	content: '';
	display: inline-block;
	height: 0.45em;
	left: 0.15em;
	position: relative;
	top: 0.45em;
	transform: rotate(-45deg);
	vertical-align: top;
	width: 0.45em;
}
.chevron.right:before {
	left: 0;
	transform: rotate(45deg);
}
.chevron.bottom:before {
	top: .15em;
	transform: rotate(135deg);
}
.chevron.left:before {
	left: 0.25em;
	transform: rotate(-135deg);
}
</style>
<script>

import LatestTransactionsChart from './components/LatestTransactionsChart.vue';
import TransactionBreakdownChart from './components/TransactionBreakdownChart.vue';
import TransactionDetailsGrid from './components/TransactionDetailsGrid.vue';
import TotalSalesSpark from "./components/TotalSalesSpark.vue";
import TypeOfClientsChart from "./components/TypeOfClientsChart.vue";
import TypeOfCategoriesChart from "./components/TypeOfCategoriesChart.vue";
import TypeOfCategoriesTrChart from "./components/TypeOfCategoriesTrChart.vue";
import ExpenseOfClientsChart from "./components/ExpenseOfClientsChart.vue";
import axios from 'axios'
export default {
  name: 'app',
  components: {
    LatestTransactionsChart,
    TransactionBreakdownChart,
    TransactionDetailsGrid,
    TotalSalesSpark,
    TypeOfClientsChart,
    ExpenseOfClientsChart,
    TypeOfCategoriesChart,
    TypeOfCategoriesTrChart 
  },
  data() {
    return {
      tit:"Cantidad total de clientes",
      tit2:"Monto total en millones de Q de transacciones ",
      tit3:"Cantidad total de transacciones",
      info:null,
      info2:null,
      info3:null
    }
  },
  methods:{
    async algo(){
      const a = await axios
      .get('http://tectestapi.azurewebsites.net/summary')
      this.info = a.data.clients;
      this.info = a.data.amount;
      this.info = a.data.transaction;
      
    }
  },
  async created() {
    this.algo();
      /* axios
      .get('http://tectestapi.azurewebsites.net/summary')
      .then(response =>
      (this.info = response.data.clients)
      ).catch(error => this.info = error)*/
  }
}
</script>
