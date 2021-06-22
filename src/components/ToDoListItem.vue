<template>
    <li 
        :class="{'finishedTask':item.finished}">
        <input type="checkbox" :checked="item.finished" />
        <a :href="'?id=' + item.id">show</a>
        {{item.name}}
      </li>
</template>

<script>
export default {
    name: "ToDoListItem",
    props: [ 'item' ]
}
</script>

<style>

</style>