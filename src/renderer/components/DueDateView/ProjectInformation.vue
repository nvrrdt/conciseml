<template>
  <div>
    <b-form @submit="onSubmit" @reset="onReset">
      <b-form-group id="projectgroup"
                    label="Project"
                    label-for="projectlabel"
                    horizontal>
        <b-form-input id="projectlabel"
                      type="text"
                      v-model="project.project">
        </b-form-input>
      </b-form-group>
      <b-form-group id="cat1group"
                    label="First categories"
                    label-for="cat1label"
                    horizontal>
        <div v-for="(cat1, index1) in getCategories1(index)" :key="cat1">
          <b-input-group>
            <b-input-group-prepend>
              <b-badge v-bind:style="{ background: getColors1(cat1) }">&nbsp;</b-badge>
            </b-input-group-prepend>
            <b-form-input id="cat1label"
                        type="text"
                        v-model="getCategories1(index)[index1]"
                        readonly>
            </b-form-input>
          </b-input-group>
        </div>
      </b-form-group>
      <b-form-group id="cat2group"
                    label="Second categories"
                    label-for="cat2label"
                    horizontal>
        <div v-for="(cat2, index2) in getCategories2(index)" :key="cat2">
          <b-input-group>
            <b-input-group-prepend>
              <b-badge v-bind:style="{ background: getColors2(cat2) }">&nbsp;</b-badge>
            </b-input-group-prepend>
            <b-form-input id="cat2label"
                        type="text"
                        v-model="getCategories2(index)[index2]"
                        readonly>
            </b-form-input>
          </b-input-group>
        </div>
      </b-form-group>
      <b-form-group id="duedategroup"
                    label="Due date"
                    label-for="duedatelabel"
                    horizontal>
        <b-form-input id="duedatelabel" type="text" v-model="project.duedate"></b-form-input>
      </b-form-group>
    </b-form>
  </div>
</template>

<script>
export default {
  props: ['project', 'index', 'getCategories1', 'getCategories2', 'getColors1', 'getColors2'],
  data () {
    return {
      selected1: null,
      selected2: null,
      selected: null
    }
  },
  methods: {
    onSubmit (evt) {
    },
    onReset (evt) {
    }
  }
}
</script>