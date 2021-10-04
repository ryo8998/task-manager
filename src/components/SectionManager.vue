<template>
    <div class="container-fluid">
        <div class="d-flex justify-content-start flex-wrap">
            <section-card v-for="section in sections" :key="section.sectionId" :section="section" @delete="deleteSection"></section-card>
            <div>
                <button class="btn btn-lg btn-secondary" @click="addSection">New Section</button>
            </div>
        </div>  
    </div>
</template>



<script>
// import MyButton from './MyButton.vue';
// import SectionCard from './components/SectionCard.vue'
import SectionCard from './SectionCard.vue';
export default {
    name:"SectionManager",
    components: { SectionCard},
        data:function(){
        return {
            sections: [],
            sectionCount:1,
            sectionForm:false,
            targetSection:"",
            colorPalette:["#B0C7BD","#F7F0F5","#F0F3BD","#D9FFF8","#7A918D","#FCD0A1","D9D7DD","#B8EBD0","#F0A7A0"]
        }
    },
    methods:{
        showSectionForm(){
            this.sectionForm=true;
        },
        unshowSectionForm(){
            this.sectionForm=false;
        },
        addSection(){
            let newSection = {
                sectionId: "s"+this.sectionCount,
                sectionName:"",
                sectionColor:this.colorPalette[this.sectionCount%this.colorPalette.length],
            };
            this.sections.push(newSection);
            this.sectionCount ++;
        },
        deleteSection(sectionId){
            console.log(sectionId);
            this.sections = this.sections.filter(section=> section.sectionId !== sectionId);
        },
        // addTask(newTask){
        //     let selectedSection = this.sections.find(ele=>ele.sectionId===newTask.parent);
        //     selectedSection.tasks.push(newTask)
        // }
    }
}
</script>