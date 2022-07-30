<template>
  <div class="home">
    <h1>Home</h1>
    <FilterNav @filterValue="current=$event" :current="current"></FilterNav>
    <div v-for="project in filteredProjects" :key="project.id">
      <SingleProject :project="project" @delete="deleteItem" @complete="completeItem"></SingleProject>
    </div>
  </div>
  
</template>

<script>
import FilterNav from '../components/FilterNav'
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
      projects : [],
      current: "all"
    }
  },
  components: {
    FilterNav,
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
  },
  computed:{
    filteredProjects(){
      if(this.current==="complete"){
        return this.projects.filter((p)=>{
          return p.complete
        })
        }
        if(this.current==="ongoing"){
          return this.projects.filter((p)=>{
            return !p.complete
          })
          }
          return this.projects
        
      
    }
  }
}
</script>
