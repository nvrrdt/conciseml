<template>
  <b-container fluid>
    <b-row>
      <b-button size="sm" variant="primary" style="margin: 5px 5px 5px 5px" @click="setClassicView()">Classic view</b-button>
      <b-button size="sm" variant="primary" style="margin: 5px 5px 5px 5px" @click="setProjectView()">Project view</b-button>
      <!-- <b-button size="sm" variant="primary" style="margin: 5px 5px 5px 5px">History</b-button> -->
    </b-row>
    <b-row>
      <Split style="height: 100vh">
        <SplitArea :size="50">
          <classic-view v-if="classicView"></classic-view>
          <project-view v-if="projectView"></project-view>
        </SplitArea>
        <SplitArea :size="50">
          <preview-mail></preview-mail>
        </SplitArea>
      </Split>
    </b-row>
  </b-container>
</template>

<script>
import ProjectView from '@/components/DueDateView/ProjectView'
import ClassicView from '@/components/DueDateView/ClassicView'
import PreviewMail from '@/components/DueDateView/PreviewMail'

export default {
  components: {
    ClassicView,
    ProjectView,
    PreviewMail
  },
  data () {
    return {
      classicView: true,
      projectView: false
    }
  },
  methods: {
    setClassicView () {
      this.classicView = true
      this.projectView = false
    },
    setProjectView () {
      this.classicView = false
      this.projectView = true
    }
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
