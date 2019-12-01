<template>
    <v-container>
        <v-layout
                text-center
                wrap
        >
            <v-flex xs12>
                <v-img
                        :src="require('../assets/logo.svg')"
                        class="my-3"
                        contain
                        height="200"
                />
            </v-flex>

            <v-flex mb-4>
                <h1>Simple app to learn Vuetify</h1>
            </v-flex>

            <v-flex
                    mb-5
                    xs12
            >
                <v-card class="mx-auto" max-width="400" tile>
                    <v-list-item v-for="todo in todoList" :key="todo.id">
                        <v-list-item-action>
                            <v-checkbox v-model="todo.checked" color="primary" @change="check">
                            </v-checkbox>
                        </v-list-item-action>
                        <v-list-item-content>
                            <v-list-item-title class="green--text" v-if="todo.checked">{{todo.content}}</v-list-item-title>
                            <v-list-item-title class="red--text" v-if="!todo.checked">{{todo.content}}</v-list-item-title>
                        </v-list-item-content>
                    </v-list-item>
                    <v-flex mb-0>
                        <v-text-field hide-details @keyup.enter="add" v-model="newTodo" class="mx-auto" label="Add a new todo" outlined>
                        </v-text-field>
                    </v-flex>
                </v-card>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
    export default {
        name: 'HelloWorld',

        data: () => ({
            newTodo: '',
            todoList:[
                {
                    id: 1,
                    content: 'Buy something',
                    checked: false
                },
                {
                    id: 2,
                    content: 'Take a shower',
                    checked: false
                },
                {
                    id: 3,
                    content: 'Go to bed',
                    checked: false
                },
            ]
        }),
        methods: {
            add() {
                let _newTodo = this.newTodo
                let count = 0
                for (let i = 0; i < this.todoList.length; i++) {
                    count++;
                }
                this.todoList.push({id: count + 1, content: _newTodo, checked: false})
            },
            check(){
                this.todoList.checked = !this.todoList.checked
            }
        }
    };
</script>
