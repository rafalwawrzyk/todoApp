<template>
  <div>
    
    <h1>{{title}}</h1>
    <div>
       <h2>Add new task</h2>
       <form v-on:submit.prevent="addTask">
           <input type="text" v-model="tasks.name">
           <input type="submit">
       </form>
       &nbsp;
    </div>

    
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
            <td><span :class="{checked: task.done }">{{task.name}}</span></td>
            <td><button v-on:click="removeTask(task)">Delete</button></td>
        </tr>
    </tbody>    
  </div>
</template>

<script>
    export default {
        data() {
            return {
                title: 'Todos App',
                tasks: [{
                        name: 'Feed your cat, bro',
                        done:false
                    },
                    {
                        name: 'Clean this house',
                        done:false
                    }
                ]
            }
        },
        methods: {
            addTask: function() {
                 this.tasks.push({
                     name:this.tasks.name,
                     done: false
                
                 })   
            },
            removeTask:function(task){
                this.tasks.splice(this.tasks.indexOf(task),1)
            }
        }
    }

</script>

<style>
    th,
    td {
        padding: 20px;
    }
    
    .checked{
        text-decoration: line-through;
    }

</style>
