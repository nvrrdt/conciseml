<template>
  <div>
    <b-form @submit.stop.prevent="onSubmit" @reset="onReset">
      <b-form-group id="projectgroup"
                    label="Project"
                    label-for="projectlabel"
                    horizontal>
        <b-form-input id="projectlabel"
                      type="text"
                      v-model="project.project"
                      @keyup.native.stop.prevent="writeJSON(key, project)">
        </b-form-input>
      </b-form-group>
      <b-form-group id="cat1group"
                    label="First categories"
                    label-for="cat1label"
                    horizontal>
        <div v-for="(cat1, index1) in project.categories1" :key="cat1">
          <b-input-group>
            <b-input-group-prepend>
              <b-badge v-bind:style="{ background: getColors1(cat1) }">&nbsp;</b-badge>
            </b-input-group-prepend>
            <b-form-input id="cat1label"
                          type="text"
                          v-model="project.categories1[index1]"
                          readonly>
            </b-form-input>
            <b-input-group-append>
              <b-btn class="m-0 p-0"
                     style="background: lightgrey"
                     v-b-toggle="'removeCat1'"
                     v-on:click="removeCat1()">
                <icon name="minus-square" scale="2"></icon><!-- minus sign to remove categorie -->
              </b-btn>
            </b-input-group-append>
          </b-input-group>
          
        </div>
        <div>
          <b-input-group>
            <b-input-group-prepend>
              <!-- color chooser needs to be inserted --> 
              <b-form-select v-model="selectedColor1" :style="{ background: selectedColor1 }">
                <option :value="null">Choose color:</option>
                <option v-for="(color, key) in colors" :key="key" :style="{ background: color.value }">{{ color.value }}</option>
              </b-form-select>
            </b-input-group-prepend>
            <b-form-input id="cat1labeladd"
                          type="text"
                          v-model="project.categories1[index1]">
            </b-form-input>
            <b-input-group-append>
              <b-btn class="m-0 p-0"
                     style="background: lightgrey"
                     v-b-toggle="'addCat1'"
                     v-on:click="addCat1()">
                <icon name="plus-square" scale="2"></icon><!-- + sign to add a categorie -->
              </b-btn>
            </b-input-group-append>
          </b-input-group>
        </div>
      </b-form-group>
      <b-form-group id="cat2group"
                    label="Second categories"
                    label-for="cat2label"
                    horizontal>
        <div v-for="(cat2, index2) in project.categories2" :key="cat2">
          <b-input-group>
            <b-input-group-prepend>
              <b-badge v-bind:style="{ background: getColors2(cat2) }">&nbsp;</b-badge>
            </b-input-group-prepend>
            <b-form-input id="cat2label"
                          type="text"
                          v-model="project.categories2[index2]"
                          readonly>
            </b-form-input>
            <b-input-group-append>
              <b-btn class="m-0 p-0"
                     style="background: lightgrey"
                     v-b-toggle="'removeCat2'"
                     v-on:click="removeCat2()">
                <icon name="minus-square" scale="2"></icon><!-- minus sign to remove categorie -->
              </b-btn>
            </b-input-group-append>
          </b-input-group>
        </div>
        <div>
          <b-input-group>
            <b-input-group-prepend>
              <!-- color chooser needs to be inserted -->
              <b-form-select v-model="selectedColor2" :style="{ background: selectedColor2 }">
                <option :value="null">Choose color:</option>
                <option v-for="(color, key) in colors" :key="key" :style="{ background: color.value }">{{ color.value }}</option>
              </b-form-select>
            </b-input-group-prepend>
            <b-form-input id="cat2labeladd"
                          type="text"
                          v-model="project.categories2[index2]">
            </b-form-input>
            <b-input-group-append>
              <b-btn class="m-0 p-0"
                     style="background: lightgrey"
                     v-b-toggle="'addCat2'"
                     v-on:click="addCat2()">
                <icon name="plus-square" scale="2"></icon><!-- + sign to add a categorie -->
              </b-btn>
            </b-input-group-append>
          </b-input-group>
        </div>
      </b-form-group>
      <b-form-group id="duedategroup"
                    label="Due date"
                    label-for="duedatelabel"
                    horizontal>
        <b-form-input id="duedatelabel" type="text" v-model="project.duedate" @keyup.native="writeJSON(key, project)"></b-form-input>
      </b-form-group>
    </b-form>
  </div>
</template>

<script>
import Vue from 'vue'
import testcategories from './testcategories.json'
import {db} from '@/firebase'

export default {
  data () {
    return {
      testcategories: testcategories,
      project: '',
      key: '',
      selectedColor1: null,
      selectedColor2: null,
      colors: [
        { value: 'lightblue' },
        { value: 'blue' },
        { value: 'lightgreen' },
        { value: 'green' },
        { value: 'cyan' },
        { value: 'red' },
        { value: 'yellow' },
        { value: 'orange' },
        { value: 'pink' }
      ]
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
    writeJSON (key, project) {
      let updates = {}
      updates['/projects/' + key + '/project'] = project.project
      updates['/projects/' + key + '/duedate'] = project.duedate

      return db.ref().update(updates)
    }
  },
  created () {
    this.$root.$on('project', data => {
      this.project = data
    })
    this.$root.$on('key', data => {
      this.key = data
    })
  }
}
</script>

<style>
  .lightblue {
    background-color: lightblue;
  }
  .blue {
    background-color: blue;
  }
  .lightgreen {
    background-color: lightgreen;
  }
  .green {
    background-color: green;
  }
  .cyan {
    background-color: cyan;
  }
  .red {
    background-color: red;
  }
  .yellow {
    background-color: yellow;
  }
  .orange {
    background-color: orange;
  }
  .pink {
    background-color: pink;
  }
</style>
