<template>
  <div>
    <b-btn block
           class="text-left p-0 m-b-2"
           style="background: lightgrey"
           v-b-toggle="'index-'+index"
           variant="link"
           v-on:click="getProjectData(index, project)"
           v-for="(project, index) in projects"
           :key="index">
      <div class="container">
        <div class="row">
          <div class="col-3 col-md-4 col-lg-4">
            {{ project.project }}
          </div>
          <div class="col-3 col-md-3 col-lg-3">
            <span class="border border-dark">
              <b-badge pill v-for="cat1 in getCategories1(project)" :key="cat1" v-bind:style="{ background: getColors1(cat1) }">&nbsp;</b-badge>
            </span>
          </div>
          <div class="col-3 col-md-3 col-lg-3">
            <span class="border border-dark">
              <b-badge pill v-for="cat2 in getCategories2(project)" :key="cat2" v-bind:style="{ background: getColors2(cat2) }">&nbsp;</b-badge>
            </span>
          </div>
          <div class="col-3 col-md-2 col-lg-2">
            {{ project.duedate }}
          </div>
        </div>
      </div>
    </b-btn>
  </div>
</template>

<script>
  import testcategories from './testcategories.json'
  // import db from '@/datastore.js' // nedb
  import {db} from '@/firebase'

  export default {
    data () {
      return {
        testcategories: testcategories,
        projects: ''
      }
    },
    methods: {
      getProjectData (index, project) {
        this.$root.$emit('index', index)
        this.$root.$emit('project', project)
      },
      /* getProjects () { // nedb
        Vue.prototype.$db = db
      }, */
      getCategories1 (project) {
        var cat1 = project.categories1
        return cat1
      },
      getCategories2 (project) {
        var cat2 = project.categories2
        return cat2
      },
      getColors1 (cat1) {
        var color1 = this.testcategories.colors1[cat1]
        return color1
      },
      getColors2 (cat2) {
        var color2 = this.testcategories.colors2[cat2]
        return color2
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
