<template>
  <div>
    <p>{{ body }}</p>
  </div>
</template>

<script>
export default {
  data () {
    return {
      body: ''
    }
  },
  methods: {
  },
  mounted () {
    this.$root.$on('project', data => {
      this.body = data.body
    })
  }
}
</script>
