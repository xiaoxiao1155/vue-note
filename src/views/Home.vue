<template>
  <div>
    <button @click="btnClick">button</button>
    <div>{{message}}</div>
  </div>
</template>

<script>
  export default {
    name: 'Home',
    data() {
      return {
        message: ""
      }
    },
    methods:{
      btnClick() {
        this.message = "dfg"
      }
    }
  }
</script>
