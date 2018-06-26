<template>
  <b-container fluid>
    <b-row>
    <Split style="height: 100vh">
      <SplitArea :size="50">
        <collapsible-mail></collapsible-mail>
      </SplitArea>
      <SplitArea :size="50">
        <preview-mail></preview-mail>
      </SplitArea>
    </Split>
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

<style>
.b-row {
  padding-right: 0px;
  margin-right: 0px;
  padding-left: 0px;
  margin-left: 0px;
}
</style>
