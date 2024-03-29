<template>
  <div class="home">
    <div v-if="projects.length">
      <div v-for="project in projects" :key="project.id">

        <SingleProject :project="project" @delete="handleDelete" @complete ="handComplete"></SingleProject>

      </div>
    </div>
  </div>
</template>

<script>

import SingleProject from '../components/SingleProject.vue'

export default {
  name: "HomePage",
  components: {
    SingleProject
  },
  data() {
    return {
      projects:[]
    }
  },
  mounted() {
    fetch('http://localhost:3000/projects').then(res=>res.json()).then(data => this.projects = data).catch(err =>console.log(err.message)) //istek attık locale, sonra geen json'u okuduk
  },
  handleDelete(id) {
    this.projects = this.projects.filter((project) => {
      return project.id !== id
    })
  },
  handComplete(id) {
    let p = this.projects.find(project => project.id === id)
    p.complete = !p.complete;
  }
};
</script>