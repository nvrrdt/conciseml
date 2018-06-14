<template>
  <b-container fluid>
    <b-row>
      <b-col><collapsible-mail></collapsible-mail></b-col>
      <b-col><preview-mail></preview-mail></b-col>
    </b-row>
  </b-container>
</template>

<script>
import CollapsibleMail from '@/components/DueDateView/CollapsableMail'
import PreviewMail from '@/components/DueDateView/PreviewMail'

export default {
  components: {
    CollapsibleMail,
    PreviewMail
  }
}
</script>
