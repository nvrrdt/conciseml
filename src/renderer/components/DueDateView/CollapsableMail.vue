<template>
  <div role="tablist">
    <b-card no-body class="border-0" v-for="(mail, index) in mails" :key="index">
      <b-card-header header-tag="header" class="p-0 m-0" role="tab">
        <b-btn block class="text-left p-0 ml-2" v-b-toggle="'index-'+index" variant="link" v-on:click="getMailBody(index)">
          {{ mail.project }} 
          <span class="border"> {{ mail.categories1 }} </span>
          <span class="border"> {{ mail.categories2 }} </span>
          {{ mail.duedate }}
        </b-btn>
      </b-card-header>
      <b-collapse :id="'index-'+index" accordion="my-accordion" role="tabpanel">
        <b-card-body>
          <p class="card-text">
            {{ mail }}
          </p>
          <p>project, cat1 (container-badges-link), cat2, due date, list of mails</p>
        </b-card-body>
      </b-collapse>
    </b-card>
  </div>
</template>

<script>
  import Vue from 'vue'
  import testmails from './testmails.json'
  import db from '@/datastore.js'

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
      },
      getProjects () {
        Vue.prototype.$db = db
      }
    }
  }
</script>

<style>

</style>
