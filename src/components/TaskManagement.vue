<template>

    <div class="card-body d-flex flex-column align-self-center px-1" style="width: 100%;">
        <task-card v-for="task in tasks" :key="task.taskId" :task="task" @delete="deleteTask"></task-card>
        <font-awesome-icon  icon="plus" @click="addTask" class="mx-2"></font-awesome-icon>
    </div>
</template>

<script>
import TaskCard from "./TaskCard";
export default {
    name:"TaskManagement",
    components:{TaskCard},
    data:function(){
        return {
            tasks:[],
            taskCount:1,
        }
    },
    methods:{
        addTask(){
            let newTask = {
                taskId:"t"+this.taskCount,
                title:"",
                detail:"",
                
            }
            this.tasks.push(newTask);
            this.taskCount ++;
        },
        deleteTask(taskId){
            this.tasks = this.tasks.filter(ele=>ele.taskId !== taskId)
        },
    }
}
</script>