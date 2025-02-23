<template>
  <li>{{ internalMsg }} - {{ msg }}</li>
</template>
<script>
  export default {
    name: 'HelloWorld',
    props: {
      msg: String
    },
    data () {
      return {
        internalMsg: 'Hello World'
      };
    }
  }
</script>
<style></style>