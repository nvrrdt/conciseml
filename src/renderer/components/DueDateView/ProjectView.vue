<template>
  <div>
    <b-btn block
           class="text-left p-0 m-b-2"
           style="background: lightgrey"
           v-b-toggle="'index-'+index"
           variant="link"
           v-on:click="getProjectData(index)"
           v-for="(project, index) in testprojects"
           :key="index">
      <div class="container">
        <div class="row">
          <div class="col-3 col-md-4 col-lg-4">
            {{ project.project }}
          </div>
          <div class="col-3 col-md-3 col-lg-3">
            <span class="border border-dark">
              <b-badge pill v-for="cat1 in getCategories1(index)" :key="cat1" v-bind:style="{ background: getColors1(cat1) }">&nbsp;</b-badge>
            </span>
          </div>
          <div class="col-3 col-md-3 col-lg-3">
            <span class="border border-dark">
              <b-badge pill v-for="cat2 in getCategories2(index)" :key="cat2" v-bind:style="{ background: getColors2(cat2) }">&nbsp;</b-badge>
            </span>
          </div>
          <div class="col-3 col-md-2 col-lg-2">
            {{ project.duedate }} / {{ test }}
          </div>
        </div>
      </div>
    </b-btn>
  </div>
</template>

<script>
  // import Vue from 'vue'
  // import testmails from './testmails.json'
  import testcategories from './testcategories.json'
  import testprojects from './testprojects.json'
  // import db from '@/datastore.js'
  import {db} from '@/firebase'

  export default {
    data () {
      return {
        // mails: testmails, // link to real mails!!
        testprojects: testprojects,
        testcategories: testcategories,
        test: 1
      }
    },
    methods: {
      getProjectData (index) {
        this.$root.$emit('index', index)
        let vm = this
        return db.ref('test').once('value').then(function (snapshot) {
          vm.test = snapshot.val()
        })
      },
      /* getProjects () {
        Vue.prototype.$db = db
      }, */
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
