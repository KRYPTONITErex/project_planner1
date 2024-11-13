<template>
  <div class="home">
   <h2>hi there, this is HOME VIEW PAGE</h2>

   <div v-for="project in projects" :key="project.id">
      <Singleproject :project="project"></Singleproject>
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
    fetch("http://localhost:3000/projects1")
    .then((response)=>{
      return response.json()
    })
    .then((datas)=>{
      this.projects=datas
    })
    .catch(()=>{

    })
  }
}
</script>
