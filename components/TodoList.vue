<template>
    <v-container>
        <p>Todo List</p>
        <v-list>
            <v-list-item v-for="(todo, index) in props.todos" v-bind:key="index">
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
</template>

<script setup lang="ts">
interface Props {
    todos: string[]
}

const props = defineProps<Props>()

type Emits = {
    deleteTodo: [index: number]
}

const emits = defineEmits<Emits>()

const deleteTodo = (index: number) => {
    emits("deleteTodo", index)
}
</script>