<template>
  <div class="app">
    
    <h1>{{title}}</h1>
    <div class="inputNav">
       <div class="formContent">
           <form v-on:submit.prevent="addTask">
           <input class="firstInput" type="text" v-model="tasks.name" placeholder="Add Task">
           <input class="submit" type="submit">
           </form>
        </div>
       
       &nbsp;
    </div>

    <div class="listTableContainer">
        <div class="todoCont">
            <thead>
                <th>Checkmark Done</th>
                <th>Task name</th>
                <th>Delete</th>
            </thead>
            <tbody>
                <tr v-for="(task,index) in tasks">
                    <td>
                        <input class="check" type="checkbox"v-model="task.done" >
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
        width: 100vw;
    }
    
    .app {
        margin: 0 auto;
        height: 100%;
        width: 100%;
    }
    
    .listTableContainer{
        display: flex;
        justify-content: center;
        
    }
    
    form{
        width: 80%;
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-bottom: 80px;
    }
    
    .firstInput{
        width: 100%;
        height: 50px;
        font-size:30px;
        color:#bababa;
        margin-bottom: 30px;
        padding: 10px;
    }
    .submit{
        width:50%;
        background-color: #25d925;
        height: 50px;
        border: none;
        font-size:30px;
        color:#fff;
        cursor: pointer;
        padding: 10px;
    }
    
    .submit:hover{
        box-shadow: 0 3px 6px rgba(0,0,0,0.16), 0 3px 6px rgba(0,0,0,0.23);
        transition: 300ms ease-in-out;
    }
    
    .formContent {
        display: flex;
        width: 100%;
        justify-content: center;
        flex-direction: column;
        align-items: center;
        margin-bottom: 50px;
        
    }
    
    h1 {
        background-color: #1d1d1d;
        color: white;
        text-align: center;
        padding: 20px;
        margin-top:0px;
    }
    
    thead,tbody{
        width:100%;
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
        border-bottom: 1px solid #9b8282;
        font-size: 20px;
        
    }
    
    th{
        color:#020a0b;
        font-size: 25px;
        color: #bababa;
        padding: 20px;
        padding-right: 60px;
        padding-left: 60px;
        
    }
    
    td{
        border:1px solid white;
        padding: 50px;
    }
    
    button{
        background-color: #ff4444;
        border: none;
        width: 100px;
        height: 50px;
        cursor: pointer;
        color:#fff;
        
    }
    
    button:hover{
        background-color: #e00505;
        box-shadow: 0 3px 6px rgba(0,0,0,0.16), 0 3px 6px rgba(0,0,0,0.23);
        transition: 300ms ease-in-out;
    }
    
    .check{
        height: 30px;
        width: 30px;
        display: block;
        margin: 0 auto;
        cursor: pointer;
         
    }
    
    .check:hover{
        box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
        transition: 300ms ease-in-out
    }
    
    .checked {
        text-decoration: line-through #ff4444;
    }

</style>
