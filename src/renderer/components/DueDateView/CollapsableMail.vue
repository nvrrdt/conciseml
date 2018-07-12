<template>
  <div role="tablist">
    <b-card no-body class="border-0" v-for="(project, index) in testprojects" :key="index">
      <b-card-header header-tag="header" class="p-0 m-0" role="tab">
        <b-btn block class="text-left p-0 ml-2" v-b-toggle="'index-'+index" variant="link" v-on:click="getMailBody(index)">
          {{ project.project }} 
          <span class="border border-dark">
            <b-badge pill v-for="cat1 in getCategories1(index)" :key="cat1" v-bind:style="{ background: getColors1(cat1) }">&nbsp;</b-badge>
          </span>
          <span class="border border-dark">
            <b-badge pill v-for="cat2 in getCategories2(index)" :key="cat2" v-bind:style="{ background: getColors2(cat2) }">&nbsp;</b-badge>
          </span>
          {{ project.duedate }}
        </b-btn>
      </b-card-header>
      <b-collapse :id="'index-'+index" accordion="my-accordion" role="tabpanel">
        <b-card-body>
          <project-information v-bind:project="project"></project-information>
        </b-card-body>
      </b-collapse>
    </b-card>
  </div>
</template>

<script>
  import Vue from 'vue'
  // import testmails from './testmails.json'
  import testcategories from './testcategories.json'
  import testprojects from './testprojects.json'
  import ProjectInformation from '@/components/DueDateView/ProjectInformation'
  import db from '@/datastore.js'

  export default {
    components: {
      ProjectInformation
    },
    data () {
      return {
        // mails: testmails, // link to real mails!!
        testprojects: testprojects,
        testcategories: testcategories
      }
    },
    methods: {
      getMailBody (index) {
        var data = this.testprojects[index].body
        this.$root.$emit('emailBody', data)
      },
      getProjects () {
        Vue.prototype.$db = db
      },
      getCategories1 (index) {
        var cat1 = this.testprojects[index].categories1
        return cat1
      },
      getCategories2 (index) {
        var cat2 = this.testprojects[index].categories2
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
    }
  }
</script>

<style>

</style>
