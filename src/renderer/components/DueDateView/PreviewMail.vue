<template>
  <div>
    <p>{{ mailBody }}</p>
  </div>
</template>

<script>
import testprojects from './testprojects.json'

export default {
  data () {
    return {
      testprojects: testprojects,
      mailBody: ''
    }
  },
  methods: {
  },
  mounted () {
    this.$root.$on('index', data => {
      this.mailBody = this.testprojects[data].body
    })
  }
}
</script>
