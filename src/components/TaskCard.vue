<template>
    <div id="task-card" class="border rounded my-2">
        <div class="col-12 px-0" @dblclick="renameTaskTitle">
            <input  :disabled="taskTitleFilled"
                    @blur="setTaskTitle"
                    @keyup.enter="setTaskTitle"
                    v-model="taskTitle"  class="text-center px-0" type="text" placeholder="New Task Here">
        </div>
        <div class="col-12 px-0 mt-2" @dblclick="editTaskDetail">
            <textarea :disabled="taskDetailFilled" 
                        @blur="setTaskDetail" 
                        @keyup.enter = "setTaskDetail"
                        v-model="taskDetail"  class="px-1 text-center" rows="3" placeholder="Task Detail Here"></textarea>
        </div>
        <div class="d-flex justify-content-end my-2">
            <font-awesome-icon icon="check" :class="{checked: this.isChecked}" @click="toggleCheck" class="mx-2"></font-awesome-icon>
            <font-awesome-icon icon="star" :class="{highlight: this.isHighlight}" @click="toggleHighlight" class="mx-2" ></font-awesome-icon>
            <font-awesome-icon  icon="trash-alt" @click="deleteTask" class="mx-2"></font-awesome-icon>
        </div>
    </div>
</template>

<script>
export default {
    name:"TaskCard",
    props:["task"],
    data:function(){
        return {
            taskTitle:"",
            taskTitleFilled:false,
            taskDetail:"",
            taskDetailFilled:false,
            isHighlight: false,
            isChecked :false,
        }
    },
    methods:{
        setTaskTitle(){
            if(this.taskTitle.length===0) return;
            this.taskTitleFilled = true;
        },
        renameTaskTitle(){
            this.taskTitleFilled = false;
        },
        setTaskDetail(){
            if(this.taskDetail.length===0) return;
            this.taskDetailFilled = true;
        },
        editTaskDetail(){
            this.taskDetailFilled = false;
        },
        deleteTask(){
            this.$emit("delete",this.task.taskId);
        },
        toggleHighlight(){
            this.isHighlight = !this.isHighlight;
        },
        toggleCheck(){
            this.isChecked = !this.isChecked;
        },
    }
}
</script>

<style scoped>
    #task-card {
        background-color: white;
        width: 100%;
    }
    .highlight {
      color: yellow;
    }
    #task-card .checked {
    color: green;
    }
    textarea, input {
        width:100%;
        border:black 1px solid;
    }
    input[disabled] {
        border:black solid 0px;
        border-bottom: grey 1px solid;
        font-size:1.2rem;
        color:black;
        font-weight: bold;
        background-color: rgba(255,255,255,0);
    }
    textarea[disabled] {
        border:transparent;
        color:black;
        background-color: rgba(255,255,255,0);
    }
</style>