<template>
  <div class="home">
    <div class="content">
      <water-polo :dataValue="dataValue" :colorList="colorList"></water-polo>
    </div>
  </div>
</template>

<script>
import waterPolo from "@/components/water-polo";
export default {
  name: "home",
  components: { waterPolo },
  data() {
    return {
      dataValue: 0.45,
      colorList: [
        "rgba(0, 159, 232, 0.3)",
        "rgba(0, 159, 232, 0.6)",
        "rgba(0, 159, 232, 1)",
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.home {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #202020;
  .content {
    width: 300px;
    height: 300px;
  }
}
</style>