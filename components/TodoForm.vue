<template>
    <v-container>
        <NuxtLink v-bind:to="{ name: 'index' }">Back</NuxtLink>
        <v-text-field placeholder="Input here" v-model="newTodo"></v-text-field>
        <v-btn v-on:click="addTodo">Add</v-btn>
    </v-container>
</template>

<script setup lang="ts">
const newTodo = ref("")

const addTodo = (): void => {
    const todos = useCookie("todos")
    todos.value.push(newTodo.value)
    newTodo.value = ""
}
</script>