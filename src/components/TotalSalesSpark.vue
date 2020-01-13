<template>
  <div class="scorecard" @mouseleave="setGuide">

    <div class="scorecard__value">{{val}}</div>
    <div class="scorecard__header">{{textTit}}</div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  props: {
    values: {
      type: Array,
      required: false
    },
    formatter: {
      type: Function,
      required: false
    },
    type: {
      type: String,
      default: "line"
    },
    start: {
      type: Date
    },
    end: {
      type: Date
    },
    textTit:{
      type:String
    },
    typee:{
      type:String
    },
    val:{
      type: Number
    }
  },

  data() {
    return {
      currentValue: 150000,
      //textTit: "",
    };
  },
   methods:{
    async algo(){
      const a = await axios
      .get('http://tectestapi.azurewebsites.net/summary')
      this.info = a.data.clients;
      
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
};
</script>

<style scoped>
</style>