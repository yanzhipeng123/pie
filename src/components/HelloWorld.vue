<template>
  <div class="hello">
    <div class="box" ref="myCharts">
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "Welcome to Your Vue.js App"
    };
  },
  mounted() {
    const my = this.$echarts.init(this.$refs.myCharts);
    let options = {
      //  backgroundColor: 'rgba(0,0,0,7)',
      title: {
        // text: "考试"
      },
        legend: {
            orient: 'vertical',
            x: 'right',
            y:'center',
            data: ['考点专练','套卷练习','仿真考试']
        },//图例属性，以饼状图为例，用来说明饼状图每个扇区，data与下边series中data相匹配
      series: [
        {
          name: "用户统计", //tooltip提示框中显示内容
          type: "pie", //图形类型，如饼状图，柱状图等
          radius: ["35%", "65%"], //饼图的半径，数组的第一项是内半径，第二项是外半径。支持百分比，本例设置成环形图。具体可以看文档或改变其值试
          data: [
            { value: 25, name: "考点专练" },
            { value: 25, name: "套卷练习" },
            { value: 25, name: "仿真考试" }
          ], 
          color: ["#f5b26c", "#54bbab", "#a3e9a5"] //各个区域颜色
        } //数组中一个{}元素，一个图，以此可以做出环形图
      ],
      graphic:{       //图形中间文字
            type:"text",
            left:"center",
            top:"center",
            style:{
                text:"做题数",
                textAlign:"center",
                fill:"#282828",
                fontSize:16
            },
            backgroundColor:'#e4e5e7'
        }
    };
    my.setOption(options);
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.box {
  width: 600px;
  height: 400px;
}
</style>
