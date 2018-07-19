<template>
  <div>
    <b-form @submit.stop.prevent="onSubmit" @reset="onReset">
      <b-form-group id="projectgroup"
                    label="Project"
                    label-for="projectlabel"
                    horizontal>
        <b-form-input id="projectlabel"
                      type="text"
                      v-model="project"
                      @keyup.native.stop.prevent="writeJSON()">
        </b-form-input>
      </b-form-group>
      <b-form-group id="cat1group"
                    label="First categories"
                    label-for="cat1label"
                    horizontal>
        <div v-for="(cat1, index1) in categories1" :key="cat1">
          <b-input-group>
            <b-input-group-prepend>
              <b-badge v-bind:style="{ background: getColors1(cat1) }">&nbsp;</b-badge>
            </b-input-group-prepend>
            <b-form-input id="cat1label"
                          type="text"
                          v-model="categories1[index1]"
                          readonly>
            </b-form-input>
          </b-input-group>
        </div>
      </b-form-group>
      <b-form-group id="cat2group"
                    label="Second categories"
                    label-for="cat2label"
                    horizontal>
        <div v-for="(cat2, index2) in categories2" :key="cat2">
          <b-input-group>
            <b-input-group-prepend>
              <b-badge v-bind:style="{ background: getColors2(cat2) }">&nbsp;</b-badge>
            </b-input-group-prepend>
            <b-form-input id="cat2label"
                          type="text"
                          v-model="categories2[index2]"
                          readonly>
            </b-form-input>
          </b-input-group>
        </div>
      </b-form-group>
      <b-form-group id="duedategroup"
                    label="Due date"
                    label-for="duedatelabel"
                    horizontal>
        <b-form-input id="duedatelabel" type="text" v-model="duedate" @keyup.native="writeJSON()"></b-form-input>
      </b-form-group>
    </b-form>
  </div>
</template>

<script>
import testcategories from './testcategories.json'
import testprojects from './testprojects.json'

export default {
  data () {
    return {
      testcategories: testcategories,
      testprojects: testprojects,
      index: '',
      project: '',
      categories1: '',
      categories2: '',
      duedate: ''
    }
  },
  methods: {
    onSubmit (evt) {
    },
    onReset (evt) {
    },
    getColors1 (cat1) {
      var color1 = this.testcategories.colors1[cat1]
      return color1
    },
    getColors2 (cat2) {
      var color2 = this.testcategories.colors2[cat2]
      return color2
    },
    writeJSON () {
      var json = JSON.stringify(this.testprojects, null, 4)
      // obj.table.push
      console.log('test')
      var fs = require('fs')
      var vm = this
      fs.writeFile('./src/renderer/components/DueDateView/testprojects.json', json, 'utf8', function (error) {
        if (error) {
          console.log('Failed' + error)
        } else {
          console.log('Written to disk: success')
        }
      })
    }
  },
  mounted () {
    this.$root.$on('index', data => {
      this.index = data
      this.project = this.testprojects[data].project
      this.categories1 = this.testprojects[data].categories1
      this.categories2 = this.testprojects[data].categories2
      this.duedate = this.testprojects[data].duedate
    })
  },
  computed: {
  }
}
</script>