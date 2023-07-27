<template>
  <div class="page">
    <!-- 此间为自己组件的演示-->
    <div class="set-value">
      <p>设置value</p>
      <cycle-progress :value="20"></cycle-progress>
    </div>
    <div class="set-size">
      <p>设置环形大小</p>
      <cycle-progress :value="20" :size="60"></cycle-progress>
    </div>
    <div class="set-border-width">
      <p>设置进度条宽度</p>
      <cycle-progress :value="20" :border-width="20"></cycle-progress>
    </div>
    <div class="set-border-color">
      <p>设置进度条颜色</p>
      <cycle-progress :value="20" :color="'#f00'"></cycle-progress>
    </div>
    <div class="set-text-size">
      <p>设置文字大小</p>
      <cycle-progress :value="20" :text-size="10"></cycle-progress>
    </div>
    <div class="set-upload">
      <p>模拟上传</p>
      <cycle-progress :value="dynamicValue" :color="'#f00'"></cycle-progress>
    </div>
    <div class="btn-container">
      <button class="upload-btn" @click="progressRun">模拟上传文件</button>
    </div>
    <!-- 此间为自己组件的演示 -->
  </div>
</template>
<script>
// 页面公用头 请勿删除
import cycleProgress from "../../components/cycle-progress";
export default {
  name: "cycle-progress-demo",
  data() {
    return {
      dynamicValue: 0,
      timer: null,
    };
  },
  computed: {},
  methods: {
    progressRun() {
      this.timer = requestAnimationFrame(this.run);
    },
    run() {
      if (this.dynamicValue < 100) {
        this.dynamicValue += 1;
        this.timer = requestAnimationFrame(this.run);
      } else {
        cancelAnimationFrame(this.timer);
      }
    },
  },
  components: {
    cycleProgress,
  },
  mounted() {},
  created() {},
};
</script>
<style lang="less" scoped>
.upload-btn {
  width: 6rem;
  height: 2rem;
  background: rgb(92, 133, 211);
  margin: 1rem;
  text-align: center;
  line-height: 2rem;
  font-size: 0.8rem;
  color: #fff;
}
</style>
