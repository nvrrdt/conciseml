<template>
  <div role="tablist">
    <b-card no-body class="mb-1" v-for="(mail, index) in mails" :key="index">
      <b-card-header header-tag="header" class="p-1" role="tab">
        <b-btn block v-b-toggle="'index-'+index" variant="link" v-on:click="getMailBody(index)">{{ mail.title }}</b-btn>
      </b-card-header>
      <b-collapse :id="'index-'+index" accordion="my-accordion" role="tabpanel">
        <b-card-body>
          <p class="card-text">
            {{ mail }}
          </p>
        </b-card-body>
      </b-collapse>
    </b-card>
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
      getMailBody (index) {
        var data = this.mails[index].body
        this.$root.$emit('emailBody', data)
      }
    }
  }
</script>