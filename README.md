# vue-echarts

> ECharts Components for Vue.js 

## İnstallation 

    npm i -S v-echarts

[Demo](https://echart-vue.herokuapp.com/)

##Use
	// Vue Template
	
	<Echartsv classname="chart-style" :options.sync="options"></Echartsv>
 
    //JS
    import Echartsv from './components/Echartsv';
    
    export default {
       data () {
        return {
	         option = {
			    tooltip: {
			        trigger: 'item',
			        formatter: "{a} <br/>{b}: {c} ({d}%)"
			    },
			    legend: {
			        /*
			            TODO : Change show key 
			        */
			        show:false,
			        orient: 'vertical',
			        x: 'left',
			        data:['data-one','data-two']
			    },
			    series: [
			        {
			            name:'chart-name',
			            type:'pie',
			            radius: ['50%', '70%'],
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
			                {value:335, name:'data-one'},
			                {value:310, name:'data-two'},
			            ]
			        }
			    ]
			}
        }
      },
      //Register Component
      components: {
        Echartsv
      }
    }
   
    
	 //css
     .chart-style{
       width: 600px;
       height: 300px;
       float: none;
       clear: both;
     }


##Options 


Option object is required so It can be referenced from [Echarts Library](https://ecomfe.github.io/echarts/doc/doc-en.html)

##Classname
Default classname `___charts___` this property `height: 400px;`

## Build Setup Development

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

```


