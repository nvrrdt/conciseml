<template>
  <b-container fluid>
    <Split style="height: 100vh">
      <SplitArea :size="50">
        <collapsible-mail></collapsible-mail>
      </SplitArea>
      <SplitArea :size="50">
        <preview-mail></preview-mail>
      </SplitArea>
    </Split>
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
