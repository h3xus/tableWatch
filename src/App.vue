<template>
  <div id="app">
    <div>
      <TableComp v-cloak />
    </div>
  </div>
</template>

<script>
import TableDataJSON from './getParts.json'
import TableComp from './components/TableComp.vue'

export default {
  name: 'app',
  components: {
    TableComp
  },
  data() {
    return {

    }
  },
  methods: {
  },
  mounted() {
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
