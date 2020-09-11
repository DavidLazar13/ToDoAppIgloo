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
                <div v-for="(todo, index) in todos" :key="todo.id" class="d-flex justify-content-between align-items-center my-3 bg-white shadow-sm rounded">
                    <div class="pl-2">
                        <input type="checkbox" id="checkbox2" class="btn btn-success" v-model="todo.done">
                        <span :class="{completed : todo.done}">{{todo.title}}</span>
                    </div>
                    <div>
                        <button type="button" class="btn btn-warning" @click="removeTodo(index)">x</button>
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
                    done: false
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

.completed{
    text-decoration: line-through;
    color: green;
}

/* checkbox */

    label {
  font-size: 20px;
}

label > input[type="checkbox"] {
  margin-top: -1px;
  margin-right: 7px;
}

input[type="checkbox"] {
  visibility: hidden;
  height: 16px;
  width: 16px;
  cursor: pointer;
}
input[type="checkbox"]:after {
  background: url("https://s3.amazonaws.com/jcgertigpublicimages/unchecked.png") no-repeat;
  background-size: contain;
  visibility: visible;
  display: block;
  content: "";
  height: 16px;
  width: 16px;
}
input[type="checkbox"]:checked:after {
  background: url("https://s3.amazonaws.com/jcgertigpublicimages/checked.png") no-repeat;
  background-size: contain;
}
input[type="checkbox"][readonly]:after, input[type="checkbox"][disabled]:after, input[type="checkbox"][readonly]:hover:after, input[type="checkbox"][disabled]:hover:after {
  background-color: inherit;
  background: url("https://s3.amazonaws.com/jcgertigpublicimages/unchecked.png") no-repeat;
  background-size: contain;
}
input[type="checkbox"][readonly]:checked:after, input[type="checkbox"][disabled]:checked:after {
  background: url("https://s3.amazonaws.com/jcgertigpublicimages/inactive-checked.png") no-repeat;
  background-size: contain;
}
input[type="checkbox"] + label {
  padding-left: 0px;
}
</style>