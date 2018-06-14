<template>
  <div>
    <p>{{ mailBody }}</p>
  </div>
</template>

<script>
import testmails from '@/components/DueDateView/testmails.json'

export default {
  data () {
    return {
      mailBody: testmails
    }
  },
  methods: {
  }
}
</script>
