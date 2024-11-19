<template>
  <h1>Edit Project</h1>

    <form v-on:submit.prevent="addProj" class="project-form">
            <label for="project-title" class="form-label">Project Title</label>
            <input v-model="title" id="project-title" type="text" class="form-input" placeholder="Enter project title">
    
            <label for="project-details" class="form-label">Project Details</label>
            <input v-model="detail" id="project-details" type="text" class="form-input" placeholder="Enter project details">
    
            <button @click="updateproject" type="submit" class="submit-button">Update Project</button>
    </form>


</template>

<script>
// import { isConcatSpreadable } from 'core-js/fn/symbol';

export default {
    props:["id"],
    data(){
        return{
            title:"",
            detail:""
        }
    },
    mounted(){
        // console.log(this.id)
        fetch('http://localhost:3000/projects/'+this.id)
        .then((res)=>{
            return res.json()
            // console.log(response)
        })
        .then((datas)=>{
            this.title=datas.title;
            this.detail=datas.detail;
        })
        .catch((err)=>{
            console.log(err);
        })
    },
    methods: {
        updateproject(){
            // console.log("Hi")
            fetch('http://localhost:3000/projects/'+this.id,{
                method:'PATCH',
                hearders:{
                    'Content-Type':'application/json'
                },
                body:JSON.stringify(
                    {
                        title:this.title,
                        detail:this.detail
                    }
                )
            })
            .then(()=>{
                this.$router.push("/")
            })
            .catch((err)=>{
                console.log(err)
            })
        }
    }

}
</script>

<style>

</style>