<template>
  <div class="home">
   <h2>hi there, this is HOME VIEW PAGE</h2>

   <div v-for="project in projects" :key="project.id">
      <Singleproject :project="project" @delete="deletePj" @complete="complete"></Singleproject>
   </div>

  </div>
</template>

<script>


import Singleproject from '../components/Singleproject'
export default {
  name: 'HomeView',
  components: {
    Singleproject,
    
  },
  data(){
    return{
      projects: [] //[{},{},{}]
    }
  },
  mounted(){
    fetch("http://localhost:3000/projects")
    .then((response)=>{
      return response.json()
    })
    .then((datas)=>{
      this.projects=datas
    })
    .catch((err)=>{
      console.log(err);
    })
  },
  methods:{
    deletePj(id){
      this.projects=this.projects.filter(project=>{
        return project.id!=id;
      })
    },
    complete(id){
      let findproj = this.projects.find(project=>{
        return project.id===id;
      });
      findproj.completed=!findproj.completed
    }
  }
}
</script>
