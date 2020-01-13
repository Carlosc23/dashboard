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
      tec: [
       7681.182811127929
      ],
      com: [
       48480.6582484515
      ],
      edu:[4723.300091412507],
      sal:[25099.817027381265],
      trans:[39691.896127495515],
      ent:[13312.334138606931],
      via:[28166.760404928962],
      mas:[1388.049712945896],
      mod:[27162.494086916395],
      otr:[3456210.3248616913],
      hog:[56403.067627020166],
      ret:[36753.051129319676]
      /*{"amount":[{"_id":"TECNOLOGÍA Y COMUNICACIONES","mnt_trx_mm":7681.182811127929},{"_id":"COMIDA","mnt_trx_mm":48480.6582484515},
      {"_id":"EDUCACIÓN","mnt_trx_mm":4723.300091412507},{"_id":"SALUD Y CUIDADO PERSONAL","mnt_trx_mm":25099.817027381265},
      {"_id":"TRANSPORTE","mnt_trx_mm":39691.896127495515},{"_id":"ENTRETENIMIENTO","mnt_trx_mm":13312.334138606931},
      {"_id":"VIAJES","mnt_trx_mm":28166.760404928962},{"_id":"MASCOTAS","mnt_trx_mm":1388.049712945896},
      {"_id":"MODA","mnt_trx_mm":27162.494086916395},{"_id":"OTROS","mnt_trx_mm":3456210.3248616913},
      {"_id":"HOGAR","mnt_trx_mm":56403.067627020166},{"_id":"RETIROS EN EFECTIVO","mnt_trx_mm":36753.051129319676}]}*/

    };
  },
  computed: {
    chartConfig() {
      return {
        type: "bar",
        title: {
          text: "Monto total gastado por categoría"
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
          text: "Q%v %t",
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