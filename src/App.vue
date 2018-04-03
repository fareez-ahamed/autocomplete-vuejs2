<template>
  <div id="app" class="container">
    <autocomplete ref="autocompleteComponent" :suggestions="suggestions" v-model="selection" :threshold="0.3"></autocomplete>
  </div>
</template>

<script>
import Autocomplete from './components/Autocomplete'

export default {
  name: 'app',
  components: {
    Autocomplete
  },
  data () {
    return {
      selection: '',
      suggestions: [
        { name: 'Bangalore', description: 'Karnataka' },
        { name: 'Chennai', description: 'Tamil Nadu' },
        { name: 'Delhi', description: 'Delhi' },
        { name: 'Kolkata', description: 'West Bengal' },
        { name: 'Mumbai', description: 'Maharashtra' },
        { name: 'LAGOS', description: 'Lagos' }
      ]
    }
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
