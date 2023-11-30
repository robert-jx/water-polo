<template>
  <div class="water-polo" ref="cpu"></div>
</template>

<script>
import * as echarts from "echarts";
import echartsLiquidfill from "echarts-liquidfill";
export default {
  name: "water-polo",
  props: {
    dataValue: {
      type: Number,
      default: 0.25,
    },
    colorList: {
      type: Array,
      default: () => [
        "rgba(0, 159, 232, 1)",
        "rgba(250, 173, 20, 1)",
        "rgba(248, 9, 65, 1)",
      ],
    },
    // 背景颜色
    backGroundColor: {
      type: String,
      default: "transparent",
    },
    // 文本颜色
    labelColor: {
      type: String,
      default: "rgba(255,255,255,0.7)",
    },
    borderColor: {
      type: String,
      default: "rgba(0, 159, 232, 1)",
    },
    shadowColor: {
      type: String,
      default: "rgba(0, 159, 232, 0.8)",
    },
  },
  data() {
    return {};
  },
  created() {},
  mounted() {
    this.myCharts1();
  },
  methods: {
    myCharts1() {
      let myChart = echarts.init(this.$refs.cpu);
      let option = {
        series: [
          {
            type: "liquidFill",
            radius: "95%",
            waveAnimation: true,
            data: [
              {
                value: this.dataValue,
                direction: "left",
                itemStyle: {
                  normal: {
                    color: this.colorList[0],
                  },
                },
              },

              {
                value: this.dataValue - 0.05,
                direction: "right",
                itemStyle: {
                  normal: {
                    color: this.colorList[1],
                  },
                },
              },
              {
                value: this.dataValue - 0.1,
                direction: "left",
                itemStyle: {
                  normal: {
                    color: this.colorList[2],
                  },
                },
              },
            ],
            outline: {
              show: true, //是否显示轮廓 布尔值
              borderDistance: 1, // 外部轮廓与图表的距离 数字
              itemStyle: {
                borderColor: this.borderColor, // 边框的颜色
                borderWidth: 3, // 边框的宽度
                shadowBlur: 5, //外部轮廓的阴影范围 一旦设置了内外都有阴影
                shadowColor: this.shadowColor, //外部轮廓的阴影颜色
              },
            },
            itemStyle: {
              opacity: 0.9, // 波浪的透明度
              shadowBlur: 0, // 波浪的阴影范围
            },
            backgroundStyle: {
              color: this.backGroundColor,
            },
            label: {
              // 数据展示样式
              show: true,
              color: this.labelColor,
              insideColor: "rgba(255,255,255,0.7)",
              fontSize: 20,
              fontWeight: 600,
              align: "center",
              baseline: "middle",
              position: "inside",
            },
          },
        ],
      };
      myChart.setOption(option);
    },
  },
};
</script>

<style lang="scss" scoped>
.water-polo {
  width: 100%;
  height: 100%;
}
</style>