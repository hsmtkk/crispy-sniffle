<template>
    <v-app>
        <v-app-bar>
            <v-app-bar-title>My Todo</v-app-bar-title>
        </v-app-bar>
        <v-main>
            <v-container>
                <v-text-field placeholder="Input here" v-model="newTodo"></v-text-field>
                <v-btn v-on:click="addTodo">Add</v-btn>
            </v-container>
            <v-container>
                <p>Todo List</p>
                <v-list>
                    <v-list-item v-for="(todo, index) in todos" v-bind:key="index">
                        <v-row>
                            <v-col cols="6">
                                <v-list-item-title>{{ todo }}</v-list-item-title>
                            </v-col>
                            <v-col cols="6">
                                <v-btn v-on:click="deleteTodo(index)">Del</v-btn>
                            </v-col>
                        </v-row>
                    </v-list-item>
                </v-list>
            </v-container>
        </v-main>
    </v-app>
</template>

<script setup lang="ts">
// class Todo {
//     id: number
//     content: string
//     constructor(id: number, content: string) {
//         this.id = id
//         this.content = content
//     }
// }

// const todos = ref([new Todo(1, "Alpha"), new Todo(2, "Bravo"), new Todo(3, "Charlie")])
const todos = ref(["Alpha", "Bravo", "Charlie"])

const newTodo = ref("")

const addTodo = (): void => {
    todos.value.push(newTodo.value)
    newTodo.value = ""
}

const deleteTodo = (index: number) => {
    todos.value.splice(index, 1)
}
</script>