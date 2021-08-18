<template>
  <div v-if="job">
    <h1>{{ job.title }}</h1>
    <p>the id is {{ job.id }}</p>
    <p> {{ job.details }}</p>
  </div>
  <div v-else>
      <p>Loading job Details...</p>
  </div>
</template>

<script>
export default {
    data(){
        return{
            job:null
        }
    },
    props:[
        'id'
    ],
    mounted(){
        fetch('http://localhost:3000/jobs/' + this.id)
            .then(res  => res.json())
            .then(data => this.job = data)
            .catch(err => console.log(err.message))
    }

}
</script>

<style>

</style>