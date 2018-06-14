<template>
<div>
  <div>
    <b-list-group v-for="(mail, index) in mails" :key="index">
      <b-list-group-item>
        <b-btn v-b-toggle="'index-'+index" variant="link">{{ mail.mail }}</b-btn>
        <b-collapse :id="'index-'+index" class="mt-2">
          <p>test {{ mail }} </p>
        </b-collapse>
      </b-list-group-item>
    </b-list-group>
  </div>
</div>
</template>

<script>
  import testmails from './testmails.json'

  export default {
    data () {
      return {
        mails: testmails
      }
    },
    methods: {
    }
  }
</script>