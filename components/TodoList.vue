<template>
    <v-container>
        <v-btn v-on:click="addTodo">Add</v-btn>
        <p>Todo List</p>
        <v-list>
            <v-list-item v-for="(todo, index) in todos" v-bind:key="index">
                <v-row>
                    <v-col cols="6">
                        <v-list-item-title>{{ todo }}</v-list-item-title>
                    </v-col>
                    <v-col cols="6">
                        <v-list-item-action>
                            <v-icon icon="mdi-delete" v-on:click="deleteTodo(index)" />
                        </v-list-item-action>
                    </v-col>
                </v-row>
                <v-divider />
            </v-list-item>
        </v-list>
    </v-container>
</template>

<script setup lang="ts">
const todos = useCookie("todos", {
    default: () => {
        return ["Alpha", "Bravo", "Charlie"]
    }
})

const addTodo = () => {
    navigateTo("todo-form")
}

const deleteTodo = (index: number) => {
    todos.value.splice(index, 1)
}
</script>