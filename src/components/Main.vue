<template>
  <div>
    <h1>Anonymous File Uploader System</h1>
    <div>
      <uploads-container v-on:files-uploaded="filesUploaded"></uploads-container>
    </div>
    <div>
      <uploaded-files ref="filesList" v-bind:files.sync="files"></uploaded-files>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import UploadedFiles from '@/components/UploadedFilesList'
import UploadsContainer from '@/components/UploadsContainer'

export default {
  name: 'Main',
  data () {
    return {
      files: []
    }
  },
  components: {
    UploadedFiles,
    UploadsContainer
  },
  methods: {
    filesUploaded (files) {
      this.$refs.filesList.filesUploaded(files)
    }
  }
}
</script>

<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
