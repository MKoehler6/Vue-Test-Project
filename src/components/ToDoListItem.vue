<template>
    <li 
        :class="{'finishedTask':item.finished}">
        <input type="checkbox" :checked="item.finished" />
        <button @click="toggleItem">toggle</button>
        <a :href="'?id=' + item.id">show</a>
        {{item.name}}
      </li>
</template>

<script>
export default {
    name: "ToDoListItem",
    props: [ 'item' ],
    methods: {
        toggleItem(){
            this.$emit('toggle', this.item) // emit löst event aus: 'toggle' (ToDoList.vue Zeile 6) und Parameter this.item
        }
    }
}
</script>

<style>

</style>