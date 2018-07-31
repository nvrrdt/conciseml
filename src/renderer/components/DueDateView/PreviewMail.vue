<template>
  <div>
    <p>{{ mailBody }}</p>
  </div>
</template>

<script>
import {db} from '@/firebase'

export default {
  data () {
    return {
      mailBody: ''
    }
  },
  methods: {
  },
  mounted () {
    this.$root.$on('index', data => {
      let vm = this

      db.ref('projects').once('value').then(function (snapshot) {
        vm.mailBody = snapshot.val()[data].body
      })
    })
  }
}
</script>
