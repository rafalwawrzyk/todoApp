<template>
  <div class="app">
    
    <h1>{{title}}</h1>
    <div class="inputNav">
       <h2>Add new task</h2>
       <div class="formContent">
           <form v-on:submit.prevent="addTask">
           <input class="firstInput" type="text" v-model="tasks.name">
           <input class="submit" type="submit">
           </form>
        </div>
       
       &nbsp;
    </div>

    <div class="listTableContainer">
        <div>
            <thead>
                <th>Checkmark Done</th>
                <th>Task name</th>
                <th>Delete</th>
                </thead>
            <tbody>
                <tr v-for="(task,index) in tasks">
                    <td>
                        <input type="checkbox"v-model="task.done" >
                    </td>
                    <td><span v-bind:class="{checked: task.done }">{{task.name}}</span></td>
                    <td><button v-on:click="removeTask(task)">Delete</button></td>
                </tr>
            </tbody>    
        </div>
        
    </div>
    
  </div>
</template>

<script>
    export default {
        data() {
            return {
                title: 'Todos App',
                tasks: [{
                        name: 'Feed your cat, bro',
                        done: false
                    },
                    {
                        name: 'Clean this house',
                        done: false
                    }
                ]
            }
        },
        methods: {
            addTask: function() {
                this.tasks.push({
                    name: this.tasks.name,
                    done: false

                })
            },
            removeTask: function(task) {
                this.tasks.splice(this.tasks.indexOf(task), 1)
            }
        }
    }

</script>

<style>
    body {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }
    
    .app {
        background-color: #b4b9be;
    }
    
    .listTableContainer{
        display: flex;
        justify-content: center;
    }
    
    .firstInput{
        width: 100vw;
        height: 50px;
        font-size:30px;
        background-color: rgba(255, 255, 255, 0.39);
        border:none;
    }
    .submit{
        
    }
    
    .formContent {
        display: flex;
    }
    
    h1 {
        background-color: #1d1d1d;
        color: white;
        text-align: center;
        padding: 20px;
    }
    
    .listTableContainer {
        width: 100%;
    }
    
    .inputNav{
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }
    
    th,
    td {
        padding: 20px;
        border: 1px solid #c92c2c;
    }
    
    .checked {
        text-decoration: line-through;
    }

</style>
