<template>
    <div class="container">
        <div class="row d-flex justify-content-center">
            <div class="col-6">
                <input type="email" class="form-control" id="exampleInputEmail1" placeholder="Your tasks here" aria-describedby="emailHelp" 
                v-model="userInput" @keyup.enter="addTodo">
            </div>
        </div>
        <div class="row d-flex justify-content-center">
            <div class="col-6">
                <div v-for="todo in todos" :key="todo.id">
                    {{todo.title}}
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
                userInput: '',
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
                alert('to do task added')
            }
        }
    }
</script>