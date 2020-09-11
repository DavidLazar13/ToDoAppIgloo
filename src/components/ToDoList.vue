<template>
    <div class="container">
        <div class="row d-flex justify-content-center">
            <div class="col-6">
                <input type="email" class="form-control" id="exampleInputEmail1" placeholder="Your tasks here" aria-describedby="emailHelp" 
                v-model="userTodo" @keyup.enter="addTodo">
            </div>
        </div>
        <div class="row d-flex justify-content-center">
            <div class="col-6">
                <div v-for="todo in todos" :key="todo.id">
                    <div>
                     {{todo.title}} <button type="button" class="btn btn-info">x</button>
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
                if(this.userTodo.trim().lenght == 0){
                    return
                }
                this.todos.push({
                    id: this.idForTodo,
                    title: this.userTodo,
                    completed: false
                })

                this.userTodo = ''
                this.idForTodo++
            }
        }
    }
</script>