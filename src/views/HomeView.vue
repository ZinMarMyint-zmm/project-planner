<template>
  <div class="home">
    <h1>Home</h1>
    <div v-for="project in projects" :key="project.id">
      <SingleProject :project="project" @delete="deleteItem" @complete="completeItem"></SingleProject>
    </div>
  </div>
</template>

<script>
import SingleProject from '../components/SingleProject'
// @ is an alias to /src


export default {
  name: 'HomeView',
  methods:{
    deleteItem(id){
      this.projects=this.projects.filter(project=>{
        return project.id!=id;
      })
    },
    completeItem(id){
      let findProject = this.projects.find(project=>{
        return project.id===id;
      })
      findProject.complete=!findProject.complete
    }
  },
  data(){
    return{
      projects : []
    }
  },
  components: {
    SingleProject,
    
  },
  mounted(){
    fetch('http://localhost:3000/projects')
    .then((response)=>{
          return response.json();
    })
    .then((datas)=>{
      this.projects=datas
    })
    .catch(()=>{

    })
  }
}
</script>
