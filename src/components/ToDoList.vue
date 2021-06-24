<template>
    <ul>
      <ToDoListItem 
        v-for="todo in todos" v-bind:key="todo.id"
        :item="todo"
        @toggle="toggleListItem"
      />  
      
    </ul>
</template>

<script>
import ToDoListItem from "./ToDoListItem"
export default {
    data: () => ({
        todos: [
           {id: 1, finished: false, name: "lernen"},
           {id: 2, finished: false, name: "Yoga"},
           {id: 3, finished: true, name: "Sport"}
    ]
    }),
    name: "ToDoList",
    components: {
        ToDoListItem
    },
    methods: {
        toggleListItem(el) {
            el.finished = !el.finished // todo erledigt oder nicht erledigt setzen
        }
    }
}
</script>

<style>

</style>