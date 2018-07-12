<template>
  <div>
    <b-form @submit="onSubmit" @reset="onReset">
      <b-form-group id="exampleInputGroup1"
                    label="Email address:"
                    label-for="exampleInput1"
                    description="We'll never share your email with anyone else.">
        <b-form-input id="exampleInput1"
                      type="email"
                      v-model="project.mail"
                      required
                      placeholder="Enter email">
        </b-form-input>
      </b-form-group>
      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
    <p class="card-text">
      {{ project.mail }}
    </p>
    <p>project, cat1 (container-badges-link), cat1 is due?, cat2, cat2 is due, due date, list of mails</p>
  </div>
</template>

<script>
export default {
  props: ['project'],
  data () {
    return {
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