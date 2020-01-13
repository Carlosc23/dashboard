<template>
  <zingchart :data="chartConfig" :theme="theme" :height="'100%'" />
</template>

<script>
import theme from "../theme/theme.js";
export default {
  props: ["data"],
  data() {
    return {
      theme,
      expectedYTD: [
       1642755.301911394
      ],
      expectedYTD2: [
       2102317.634356314
      ],
    };
  },
  computed: {
    chartConfig() {
      return {
        type: "bar",
        title: {
          text: "Gastos por cada tipo de cliente"
        },
        plot: {
          animation: {
            effect: 11,
            speed: 400,
            method: 11,
            sequence: 1
          }
        },
        series: [
          {
            values: this.expectedYTD,
            text: "Nacionales"
          },
           {
            values: this.expectedYTD2,
            text: "Extranjeros"
          }
        ],
        tooltip: {
          negation: "currency",
          text: "Q%v %t",
          "thousands-separator": ","
        },
        //legend: {},
        scaleX: {
          label: {
            text: "Nacionales/Extranjeros"
          },
        },
        scaleY: {
          short: true,
          shortUnit: "K"
        }
      };
    },

  }
};

</script>