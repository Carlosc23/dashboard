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
      tec: [36024],
      com: [366048],
      edu:[4826],
      sal:[113024],
      trans:[195946],
      ent:[68228],
      via:[36128],
      mas:[9124],
      mod:[123266],
      otr:[567133],
      hog:[291509],
      ret:[100120]
      /*{"amount":[{"_id":"TECNOLOGÍA Y COMUNICACIONES","num_trx":36024},{"_id":"COMIDA","num_trx":366048},
      {"_id":"EDUCACIÓN","num_trx":4826},{"_id":"SALUD Y CUIDADO PERSONAL","num_trx":113024},{"_id":"TRANSPORTE","num_trx":195946},
      {"_id":"ENTRETENIMIENTO","num_trx":68228},{"_id":"VIAJES","num_trx":36128},{"_id":"MASCOTAS","num_trx":9124},
      {"_id":"MODA","num_trx":123266},
      {"_id":"OTROS","num_trx":567133},{"_id":"HOGAR","num_trx":291509},{"_id":"RETIROS EN EFECTIVO","num_trx":100120}]}*/

    };
  },
  computed: {
    chartConfig() {
      return {
        type: "bar",
        title: {
          text: "Transacciones totales  por categoría"
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
            values: this.tec,
            text: "TECNOLOGÍA Y COMUNICACIONES"
          },
           {
            values: this.edu,
            text: "EDUCACIÓN"
          },
          {
            values:this.sal,
            text:"SALUD Y CUIDADO PERSONAL"
          },
          {
            values: this.com,
            text: "COMIDA"
          },
          {
            values: this.trans,
            text: "TRANSPORTE"
          },
          {
            values: this.ent,
            text: "ENTRETENIMIENTO"
          },
           {
            values: this.via,
            text: "VIAJES"
          },
           {
            values: this.mas,
            text: "MASCOTAS"
          },
          {
            values: this.mod,
            text: "MODA"
          },
          {
            values: this.otr,
            text: "OTROS"
          },
          {
            values: this.hog,
            text: "HOGAR"
          },
          {
            values:this.ret,
            text: "RETIROS EN EFECTIVO"
          }
        ],
        tooltip: {
          negation: "currency",
          text: "%v %t",
          "thousands-separator": ","
        },
        //legend: {},
        scaleX: {
          label: {
            text: "Categoria"
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