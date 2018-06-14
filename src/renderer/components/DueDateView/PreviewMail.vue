<template>
  <div>
    <p>{{ mailBody }}</p>
  </div>
</template>

<script>
export default {
  data () {
    return {
      mailBody: ''
    }
  },
  methods: {
  },
  mounted () {
    this.$root.$on('emailBody', data => {
      this.mailBody = data
    })
  }
}
</script>
