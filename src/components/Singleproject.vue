<template>

<div :class="['project', { completed: project.completed }]">
    <div class="flex">
        <h3 @click="showDetail = !showDetail" id="title">{{ project.title }}</h3>

        <div class="ICON">
            <span class="material-icons" @click="deletePj">delete_sweep</span>

            <router-link :to="{name:'EditProject',params:{id:project.id}}">
                <span class="material-icons" >drive_file_rename_outline</span>
            </router-link>

            <span class="material-icons" @click="complete">how_to_reg</span>
        </div>
    </div>

    <div class="info">
        <h4 v-if="showDetail">{{ project.detail }}</h4>
    </div>
</div>


  
</template>

<script>
import { compile } from 'vue';

export default {
    props:['project'],
    data(){
        return{
            showDetail: false,
            api: 'http://localhost:3000/projects/'
        }
    },
    methods: {
        deletePj(){
            let deleteRoute = this.api+this.project.id;
            fetch(deleteRoute,{method:"DELETE"})
            .then(()=>{
                this.$emit('delete',this.project.id)
            })
            .catch((err)=>{
                console.log(err);
            })
        },
        complete(){
            let updateStatus = this.api+this.project.id;
            fetch(updateStatus,{
                method:"PATCH",
                headers: {
                    "Content-Type":"application/json"
                },
                body:JSON.stringify(
                    {
                        completed:!this.project.completed
                    }
                )
            })
            .then(()=>{
                this.$emit('complete',this.project.id)
            })
            .catch((err)=>{
                console.log(err);
            })
        }
    }

}
</script>

<style>
#title{
    cursor: pointer;
}
.project {
    color: rgba(186, 1, 1, 0.838);
    padding: 20px 20px 10px 20px;
    background-color: rgba(254, 254, 117, 0.712);
    margin: 30px;
    border-radius: 15px;
    width: 500px;
    border-left: 15px solid rgb(250, 47, 88); /* Default color for incomplete projects */
    border-top-left-radius: 1px;
    border-bottom-right-radius: 5px;
    box-shadow: 3px 3px 3px rgb(216, 216, 216);
}

.project.completed {
    border-left: 15px solid rgba(219, 246, 12, 0.868);
    /* background-color: rgb(18, 138, 130); */
    color: rgb(21, 103, 96);
    margin-left: 100px;
    font-style: italic;
    transition: background-color 1.5s ease, border-left 1s ease;
}

.flex{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 0;
    padding: 0;
}
.info{
    padding: 0;
    margin: 0;
}
.ICON{
   display: flex;
   gap: 20px;
}
span{
    cursor: pointer;
}



</style>
