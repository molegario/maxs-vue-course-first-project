<template>
  <div>
    <h1>{{ appMsg }}</h1>
    <ul>
      <HelloWorld v-for="message in appMsgArr" :msg="message.msg" :key="message.id"/>
    </ul>
  </div>  
</template>

<script>
  import HelloWorld from './components/HelloWorld.vue'

  export default {
    name: 'App',
    components: {
      HelloWorld
    },
    data() {
      return {
        appMsg: 'Welcome to Your Vue.js App XXX',
        appMsgArr: [
          {
            id: "v001",
            msg: 'Welcome to Your Vue.js App 1',
          },
          {
            id: "v002",
            msg: 'Welcome to Your Vue.js App 2',
          },
          {
            id: "v003",
            msg: 'Welcome to Your Vue.js App 3',
          },
          {
            id: "v004",
            msg: 'Welcome to Your Vue.js App 4',
          },
          {
            id: "v005",
            msg: 'Welcome to Your Vue.js App 5',
          },
        ],
      };
    },
  }

</script>


<style>


</style>