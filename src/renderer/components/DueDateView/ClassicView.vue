<template>
  <div>
    <b-btn block
           class="text-left p-0 m-b-2"
           style="background: lightgrey"
           v-b-toggle="'index-'+index"
           variant="link"
           v-on:click="getProjectData(index)"
           v-for="(project, index) in projects"
           :key="index">
      <div>
        {{ project.title }}
      </div>
    </b-btn>
  </div>
</template>

<script>
  import {db} from '@/firebase'

  export default {
    data () {
      return {
        projects: ''
      }
    },
    methods: {
      getProjectData (index) {
        this.$root.$emit('index', index)
      }
    },
    mounted: function () {
      let vm = this

      db.ref('projects').once('value').then(function (snapshot) {
        vm.projects = snapshot.val()
      })
    }
  }
</script>

<style>

</style>
