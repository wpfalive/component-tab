<template>
  <div class="tab-navs">
    <ul @click="toggleActive">
      <li ref="sliderTab" class="slider-bar" :style="style || defaultStyle">
        <!-- <span></span> -->
      </li>
      <li v-for="(item, index) in titles"
        :ref="'title' + index"
        :id="index"
        :key="index"
        :class="{active: index === active}"
        >
        {{item}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Tab',
  props: {
    titles: Array,
    required: true
  },
  data () {
    return {
      active: 0,
      style: '',
      defaultStyle: ''
    }
  },
  methods: {
    toggleActive (e) {
      // 如果被点击的是ul，就什么也不做
      if (e.target === e.currentTarget) {
        return
      }
      this.active = parseInt(e.target.id)
      // 获取不带padding的宽度
      const elementStyle = window.getComputedStyle(e.target)
      const widthWithoutPadding = elementStyle.getPropertyValue('width')
      // 20为左侧margin
      this.style = `
        left: ${e.target.offsetLeft - 20}px;
        width: ${widthWithoutPadding};
      `
    }
  },
  mounted () {
    debugger
    console.log(this.$refs.title0[0].offsetWidth)
    this.defaultStyle = `width: ${this.$refs.title0[0].offsetWidth}px`
  }
}
</script>

<style scoped>
* {
  padding: 0;
  margin: 0;
}
ul {
  display: flex;
  position: absolute;
  width: 800px;
  top: 50%;
  left: 50%;
  x-webkit-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
}

li {
  position: relative;
  margin: 10px 20px;
  font-size: 24px;
  color: #000;
  line-height: 1;
  cursor: pointer;
  list-style: none;
}
li.active {
  font-weight: bold;
}
.slider-bar {
  position: absolute;
  left: 0;
  width: 150px;
  bottom: -10px;
  border-bottom: 1px solid black;
  transition: all .15s ease-in
}
</style>
