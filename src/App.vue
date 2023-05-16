<template>
  <div id="app">
    <div class="logo" :class="{ small: 'isFocuse' }">AI.NAV</div>

    <div class="wrapper" :class="{ up: 'isFocuse' }" ref="wrapper">
      <div class="input-data">
        <input
          type="text"
          @click="inputClick"
          @blur="inputBlur"
          v-model="input"
          required
        />
        <div class="underline"></div>
        <label>{{ tips }}</label>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import ElementUI from "element-ui";
Vue.use(ElementUI);
export default {
  data() {
    return {
      input: "",
      tips: "您需要什么AI工具，请点击这里查询",
      isFocused: false,
    };
  },
  methods: {
    inputClick() {
      this.tips = "查找关键字即可模糊搜索";
      this.isFocused = true;
      const wrapper = this.$refs.wrapper;
      const logo = document.querySelector(".logo");
      wrapper.style.transform = "translateY(-400%)";
      // logo.style.transform = "translate(-50%, -50%) scale(0.1)";
      logo.style.transform = "matrix(1, 0, 0, 1, -600, -250) translate(-50%, -50%) scale(0.5)";
      // logo.style.transform = "translateX(-500%)";
    },
    inputBlur() {
      this.tips = "您需要什么AI工具，请点击这里查询";
      this.isFocused = false;
      const wrapper = this.$refs.wrapper;
      const logo = document.querySelector(".logo");
      wrapper.style.transform = "";
      logo.style.transform = "";
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  outline: none;
  background: linear-gradient(deg, #ffffff, #f3f6ff);
}
#app {
  width: 100vw;
  min-height: 100vh;
  gap: 10vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
/* 输入框 */
.wrapper {
  width: 750px;
  background-color: #fff;
  /* 内边距（上下左右） */
  padding: 25px;
  /* 盒子阴影 */
  box-shadow: 2px 5px 10px rgba(0, 0, 0, 0.1);
  /* 圆角 */
  border-radius: 10px;
  transition: transform 0.6s ease; /* 添加过渡效果 */
}
.wrapper .input-data {
  /* 相对定位 */
  position: relative;
  width: 100%;
  height: 60px;
}
.wrapper .input-data input {
  width: 100%;
  height: 100%;
  border: none;
  font-size: 30px;
  border-bottom: 2px solid #727272;
}
/* 输入框获得焦点时 */
.wrapper .input-data input:focus ~ label,
/* 输入框的值为合法时 */
.wrapper .input-data input:valid ~ label {
  /* label上移，同时改变字号、字体颜色 */
  transform: translateY(-45px);
  font-size: 25px;
  color: #0db19b;
}

.wrapper .input-data label {
  opacity: 0.8;
  /* 绝对定位 */
  position: absolute;
  font-size: 30px;
  bottom: 10px;
  left: 0px;
  color: #6e6e6e;
  /* 这个属性可以使点击label穿透到输入框 */
  pointer-events: none;
  /* 现在动画有点生硬，在这里需要给动画加个过渡 */
  transition: all 0.6s ease;
}
.wrapper .input-data .underline {
  position: absolute;
  bottom: 0px;
  height: 3px;
  width: 100%;
  background-color: #0db19b;
  /* 沿X轴缩小 */
  transform: scaleX(0);
  /* 这里同样给动画加个过渡 */
  transition: all 0.6s ease;
}
.wrapper .input-data input:focus ~ .underline,
.wrapper .input-data input:valid ~ .underline {
  /* 沿X轴放大 */
  transform: scaleX(1);
}
.wrapper .input-data input:hover ~ .underline{
    /* 沿X轴放大 */
  transform: scaleX(1);
}

/* LOGO */
.logo {
  font-size: 36px; /* 调整字体大小 */
  font-weight: bold; /* 加粗字体 */
  letter-spacing: 2px; /* 字符间距 */
  color: #333; /* 字体颜色 */
  text-transform: uppercase; /* 转换为大写字母 */
  /* animation: active; */
   transition: transform 0.6s ease; /* 添加过渡效果 */
}
</style>
