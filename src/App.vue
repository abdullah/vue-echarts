<template>
    <div class="container">
      
      <div>
        <label for=""><span>Radius one</span><input type="text" v-model="radiusone"></label>
        <label for=""><span>Radius two</span><input type="text" v-model="radiustwo"></label>
        <label for=""><span>node</span><input type="text" v-model="node"></label>
        <label for=""><span>php</span><input type="text" v-model="php"></label>
        <label for=""><span>bash</span><input type="text" v-model="bash"></label>
        <label for=""><span>java</span><input type="text" v-model="java"></label>
        <label for=""><span>other</span><input type="text" v-model="other"></label>
      </div>
      
      <Echartsv classname="chart-style" :options.sync="options"></Echartsv>

    </div>
</template>

<script>
import Echartsv from './components/Echartsv';

import _ from 'lodash'

export default {
   data () {
    return {
      radiusone:50,
      radiustwo:70,
      node:100,
      php:100,
      bash:100,
      java:100,
      other:100,
    }
  },
  computed:{
    'options':function () {
      var radiusone = this.radiusone+'%',
          radiustwo = this.radiustwo+'%',
          node = this.node,
          php = this.php,
          bash = this.bash,
          java = this.java,
          other = this.other;
      return {
          tooltip: {
              trigger: 'item',
              formatter: "{a} <br /> {b}: {c} ({d}%)"
          },
          legend: {
              /*
                TODO : Change show key 
              */
              show:false,
              orient: 'vertical',
              x: 'cenge',
              data:['nodejs','php','bash','java','other']
          },
          series: [
              {
                  name:'Game Of Language',
                  type:'pie',
                  radius: [radiusone, radiustwo],
                  avoidLabelOverlap: false,
                  label: {
                      normal: {
                          show: false,
                          position: 'center'
                      },
                      emphasis: {
                          show: true,
                          textStyle: {
                              fontSize: '30',
                              fontWeight: 'bold'
                          }
                      }
                  },
                  labelLine: {
                      normal: {
                          show: false
                      }
                  },
                  data:[
                      {value:node, name:'nodejs'},
                      {value:php, name:'php'},
                      {value:bash, name:'bash'},
                      {value:java, name:'java'},
                      {value:other, name:'other'}
                  ]
              }
          ]
      }
    }
  },
  components: {
    Echartsv
  }
}
</script>

<style lang="scss">
  .container{
    max-width: 600px;
    margin: auto;
  }
  .chart-style{
    width: 600px;
    height: 300px;
    float: none;
    clear: both;
  }
  label{
    display: block;
    width: 50%;
    float: left;
    margin-bottom: 10px;
    span{
      min-width: 100px;
      display: inline-block;
      text-transform: capitalize;
      font-family: Arial;
    }
    input{
      margin-left: 10px;
    }
  }
</style>
