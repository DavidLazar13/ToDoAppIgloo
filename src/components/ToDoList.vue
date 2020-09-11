<template>
    <div class="container">
        <div class="row d-flex justify-content-center pb-3">
            <div class="col-6 d-flex flex-row">
                <input type="email" class="form-control" id="exampleInputEmail1" placeholder="What needs to be done?" aria-describedby="emailHelp" 
                v-model="userTodo" @keyup.enter="addTodo">
                <button type="button" class="btn btn-info ml-2" @click="addTodo">add</button>
            </div>
        </div>
        <div class="row d-flex justify-content-center">
            <div class="col-6">
                <div v-for="(todo, index) in todos" :key="todo.id" class="d-flex justify-content-between py-2">
                    <div>
                     {{todo.title}} 
                    </div>
                    <div>
                        <button type="button" class="btn btn-info" @click="removeTodo(index)">x</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'todo-list',
        data () {
            return{
                userTodo: '',
                idForTodo: 3, 
                todos: [
                    {
                        'id': 1,
                        'title': 'Igloo Hard Problem', 
                        'done': false
                    },
                                        {
                        'id': 2,
                        'title': 'Get grocerries', 
                        'done': false
                    }
                ]
            }
        },
        methods: {
            addTodo() {
                if(this.userTodo.trim().length == 0){
                    return
                }
                this.todos.push({
                    id: this.idForTodo,
                    title: this.userTodo,
                    completed: false
                })

                this.userTodo = ''
                this.idForTodo++
            },
            removeTodo(index) {
                this.todos.splice(index, 1)
            }
        }
    }
</script>

<style>
</style>