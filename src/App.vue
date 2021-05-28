<template>
  <div>
    <table-test2></table-test2>
  </div>
</template>

<script>
import Vue from 'vue';
import 'element-ui/lib/theme-chalk/index.css';
import UmyUi from 'umy-ui'
import 'umy-ui/lib/theme-chalk/index.css';// 引入样式
import TableTest2 from "@/components/tableTest2";
Vue.use(UmyUi)
export default {
  components:{
    TableTest2
  },
  data() {
    return {

    }
  },
  mounted () {

  },
  methods: {

  }
}
</script>
