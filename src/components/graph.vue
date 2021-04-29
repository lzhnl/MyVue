<template>
  <div id="myChart" class="myChart" :style="{width: '100%', height: '90vh'}"></div>
</template>


<script>
let echarts=require('echarts/lib/echarts')
require('echarts/lib/chart/graph')
require('echarts/lib/component/tooltip')
require('echarts/lib/component/toolbox')
require('echarts/lib/component/title')
export default {
  name: "graph",
  data(){
    return{
    }
  },
  mounted() {
  this.darw()
  },
  methods:{
  darw(){
    let myChart=echarts.init(document.getElementById('myChart'))
    let categories = [];
    myChart.setOption({
      // title:{
      //   text:'ECharts 关系图',
      //   x:'center',
      //   y:'top'
      // },
      tooltip:{formatter:function (x){return x.data.des}},
      toolbox:{
        show:true,feature:{
          mark:{show:true},
          restore:{show:true},
          saveAsImage:{show:true}
        }},
      legend:[{
        data: categories.map(function (a){return a.name})
      }],
      series: [{
        type: 'graph', // 类型:关系图
        layout: 'force', //图的布局，类型为力导图
        symbolSize: 40, // 调整节点的大小
        roam: true, // 是否开启鼠标缩放和平移漫游。默认不开启。如果只想要开启缩放或者平移,可以设置成 'scale' 或者 'move'。设置成 true 为都开启
        edgeSymbol: ['circle', 'arrow'],
        edgeSymbolSize: [2, 10],
        force: {
          repulsion: 2500,
          edgeLength: [10, 50]
        },
        draggable: true,
        lineStyle: {
          normal: {
            width: 2,
            color: '#4b565b',
          }
        },
        edgeLabel: {
          normal: {
            show: true,
            formatter: function (x) {
              return x.data.name;
            }
          }
        },
        label: {
          normal: {
            show: true,
            textStyle: {}
          }
        },

        // 数据
        data: [{
          name: 'node01',
          des: 'ip:10.12.5.186,' +
              'port:80/tcp,' +
              'service:sftp',
          symbolSize: 70,
          category: 0,
        }, {
          name: 'node02',
          des: 'nodedes02',
          symbolSize: 50,
          category: 1,
        }, {
          name: 'node03',
          des: 'nodedes3',
          symbolSize: 50,
          category: 1,
        }, {
          name: 'node04',
          des: 'nodedes04',
          symbolSize: 50,
          category: 1,
        }, {
          name: 'node05',
          des: 'nodedes05',
          symbolSize: 50,
          category: 1,
        }],
        links: [{
          source: 'node01',
          target: 'node02',
          name: 'link01',
          des: 'link01des'
        }, {
          source: 'node01',
          target: 'node03',
          name: 'link02',
          des: 'link02des'
        }, {
          source: 'node01',
          target: 'node04',
          name: 'link03',
          des: 'link03des'
        }, {
          source: 'node01',
          target: 'node05',
          name: 'link04',
          des: 'link05des'
        }],
        categories: categories,
      }]

    })
  }
  }
}
</script>

<style scoped>
#myChart{
  overflow: hidden;
}
</style>