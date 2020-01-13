<template>
   <zingchart :data="chartConfig" :theme="theme"  :height="'100%'"/> 

   
</template>

<script>
import theme from "../theme/theme.js";
export default {
  props: ['entries'],
  data() {
    return {

    };
  },
  computed: {
    acquisitionBreakdown() {
      const categories = this.entries.reduce((acc, transaction) => {
        acc[transaction.purchase_type] = acc[transaction.purchase_type] || 0;
        acc[transaction.purchase_type]++;
        return acc;
      }, {});
      return categories;
    },
    chartConfig() {
      const colorss = [
        {
          backgroundColor: '#04A3F5',
          hoverState: {
            backgroundColor: '#45D6C4'
          }
        },
        {
          backgroundColor: '#98D1EE',
          hoverState: {
            backgroundColor: '#45D6C4'
          }
        },
                {
          backgroundColor: '#295A73',
          hoverState: {
            backgroundColor: '#45D6C4'
          }
        },
      ]
      const config ={
        type: 'pie',

        tooltip: {
          text: '%npv%'
        },
        plotarea: {
          margin: '5'
        },
        plot: {
          valueBox: {
            fontSize: 10,
            text: '%t'
          },
          hoverState: {
         	  borderWidth: 2,
          }
        },
        /*series: Object.keys(this.acquisitionBreakdown).map((type, index) => {
          console.log(this.acquisitionBreakdown[type])
          return Object.assign(
            { values: [this.acquisitionBreakdown[type]], text: type},
            colors[index],
          );
        })*/
        series: [{ values: [36537],text:"Nacionales",backgroundColor: '#04A3F5',},
                  { values: [4351],text:"Extranjeros",backgroundColor: '#98D1EE',}]
      };
      return config;
    },
  }
}
</script>