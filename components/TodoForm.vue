<template>
    <v-container>
        <v-text-field placeholder="Input here" v-model="newTodo"></v-text-field>
        <v-btn v-on:click="addTodo">Add</v-btn>
    </v-container>
</template>

<script setup lang="ts">
const newTodo = ref("")

type Emits = {
    addTodo: [content: string]
}

const emits = defineEmits<Emits>()

const addTodo = (): void => {
    emits("addTodo", newTodo.value)
    newTodo.value = ""
}
</script>