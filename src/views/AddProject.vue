<template>

    <div class="add-project-page">
      <h1 class="title">Add Project Page</h1>
      
        <form v-on:submit.prevent="addProj" class="project-form">
            <label for="project-title" class="form-label">Project Title</label>
            <input v-model="title" id="project-title" type="text" class="form-input" placeholder="Enter project title">
    
            <label for="project-details" class="form-label">Project Details</label>
            <input v-model="detail" id="project-details" type="text" class="form-input" placeholder="Enter project details">
    
            <button type="submit" class="submit-button">Add Project</button>
        </form>

    </div>

</template>
  
<script>
  export default {
    name: 'AddProjectPage',
    data(){
        return{
            title:"",
            detail:""
        }
    },
    methods: {
        addProj(){
            fetch("http://localhost:3000/projects",{
                method:"POST",
                headers:{
                    "Content-Type":"application/json"
                },
                body:JSON.stringify(
                    {
                        title:this.title,
                        detail:this.detail,
                        completed: false
                    }
                )
            })
            .then(()=>{
                this.$router.push("/")

            })
            .catch((err)=>{
                console.log(err);
            })
        }
    }
  };
</script>
  
<style>
  .add-project-page {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    font-family: Arial, sans-serif;
  }
  
  .title {
    color: brown;
    font-size: 24px;
    text-align: center;
    margin-bottom: 20px;
  }
  
  .project-form {
    display: flex;
    flex-direction: column;
    gap: 15px;
  }
  
  .form-label {
    font-size: 14px;
    font-weight: bold;
  }
  
  .form-input {
    padding: 10px;
    font-size: 14px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  .form-input:focus {
    outline: none;
    border-color: #007BFF;
  }
  
  .submit-button {
    background-color: brown;
    color: white;
    font-size: 16px;
    padding: 10px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .submit-button:hover {
    background-color: darkred;
    letter-spacing: 3px;
    font-weight: bold;
  }
</style>