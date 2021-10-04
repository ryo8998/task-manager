<template>
    <div class="card col-md-3 col-lg-2 text-dark text-center bg-light mb-3 px-1 py-1 mx-3   align-self-start justify-content-center" style="max-width: 100%;">
        <div class="card-header d-flex flex-column align-items-center justify-content-center pt-1 pb-0 px-0" @click.self="setSectionName" :style="styles" >
            <div class="col-12 px-0" @dblclick="renameSectionName">
                <input :disabled="sectionFilled" 
                        @blur="setSectionName" 
                        @keyup.enter="setSectionName" 
                        v-model="sectionName" class="text-center col-10" type="text" placeholder="New Section Here">
            </div>
            <div class="d-flex align-items-end justify-content-end col-10 px-0 mt-2">
                <font-awesome-icon @click="deleteSection" icon="trash-alt" style="color:black;"></font-awesome-icon>    
            </div>
        </div>
        <task-management></task-management>
    </div>
</template>

<script>
import TaskManagement from './TaskManagement.vue'

export default {
    components:{TaskManagement},
    name:"SectionCard",
    props:["section"],
    data:function(){
        return {
            sectionFilled:false,
            sectionName:"",
            styles: {
                    backgroundColor: this.section.sectionColor,
                    color:"white",
                }
        }
    },
    methods:{
        setSectionName(){
            console.log("check")
            if(this.sectionName.length===0) return;
            this.sectionFilled = true;
        },
        renameSectionName(){
            this.sectionFilled = false;
        },
        deleteSection(){
            this.$emit("delete",this.section.sectionId)
        }
    },
}
</script>

<style scoped>
    font-awesome-icon {
        width:100%;
    }
    input[disabled] {
        border:black solid 0px;
        font-size:1.5rem;
        font-weight: bold;
        color:black;
        background-color: rgba(255,255,255,0);
    }
</style>