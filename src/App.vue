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
    <ul>
      <li v-for="(city, index) in cities" v-bind:key="city.id">
        {{++index}}. {{city.name}}
      </li>
    </ul>
    
    <div class="list">
     <ToDoList />
    <button @click="test">Test</button>
    </div>
  </div>
  
</template>

<script>
import ToDoList from "./components/ToDoList"
export default {
  name: 'App',
  data: () => ({
    name_first: 'Micha',
    name_last: 'Köhler',
    age: 49,
    cities: [
      {id: 1, name: "Stuttgart"},
      {id: 2, name: "Frankfurt"},
      {id: 3, name: "Paris"}
    ],
  }),
  computed: {
    fullName() {
      return this.name_first + " " + this.name_last;
    }
  },
  methods: {
    test() {
      alert("Hi");
    }
  },
  components: {
    ToDoList
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
.list {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
.finishedTask {
  text-decoration: line-through;
}
</style>
