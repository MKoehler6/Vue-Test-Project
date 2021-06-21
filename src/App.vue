<template>
  <div id="app">
    {{ name_first }},
    {{ `${age} ` }},
    vor 18 Jahren:  
    {{ `${age - 18}` }} <hr>
    <div class="age">
      {{ fullName }}
      <span v-if="age < 18"> <!-- span wird nur angezeigt bei if true -->
        Unter 18!
      </span>
    </div>
    <hr>
    {{ age > 17 ? 'volljährig' : 'nicht volljährig'}}
  </div>
</template>

<script>

export default {
  name: 'App',
  data: () => ({
    name_first: 'Micha',
    name_last: 'Köhler',
    age: 49
  }),
  computed: {
    fullName() {
      return this.name_first + " " + this.name_last;
    }
  }
}
</script>

<style>
.age {
  border: 1px solid #f00;
  margin: 5px;
  padding: 10px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
