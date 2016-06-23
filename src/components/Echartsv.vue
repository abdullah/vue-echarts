<template>
    <div 
        :class="[classname]" 
        id="___charts___{{_uid}}">
    </div>
</template>

<script>
// Echarts import
import echarts from 'echarts'

export default {
  props: {
   options:{
    type:Object,
    required:true,
    twoWay: true,
    validator: function (value) {
      return typeof value === 'object'
    }
   },
   classname:{
      type: String,
      default: function () {
        console.log("Classnames not found in props")
        return "___charts___";
      }
   }
  },
  data () {
    return {
      _vue_charts:null
    }
  },
  // When change data trigger updateCharts().
  watch:{
    'options':{
      handler: function (val, oldVal) { 
        this.updateCharts();
      },
      deep: true
    }
  },
  ready(){
    this.renderCharts()
  },
  methods:{
    /*
    @param null
    @return void
    */
    renderCharts:function () {
      this._vue_charts = echarts.init(document.getElementById('___charts___'+this._uid));
      this._vue_charts.setOption(this.options);
    },
    /*
    @param null
    @return void
    */
    updateCharts:function () {
      this._vue_charts.setOption(this.options);
    }

  }
}
</script>
<style>
  .___charts___{
    height: 400px;
  }
</style>