<template>
  <div>
    <tab :titles="titles"></tab>
  </div>
</template>

<script>
import Tab from '@/components/Tab'
export default {
  name: 'HelloWorld',
  components: {
    Tab
  },
  data () {
    return {
      titles: [
        '光标跟随下划线',
        '登录状态',
        'hellow',
        '注册'
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
