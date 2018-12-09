<template>
  <div>
    <div>
      <a v-bind:href="'/file/download/' + file.encodedName" v-on:click="downloadFile">{{ file.name }}</a> <button v-on:click="deleteFile(file)">Delete</button>
    </div>
    <file-downloader :key="downloadKey" ref="downloader"></file-downloader>
  </div>
</template>

<script>
import axios from 'axios'
import FileDownloader from './FileDownloader'

export default {
  props: ['file'],
  components: {
    FileDownloader
  },
  data () {
    return {
        downloadKey: 1
    }
  },
  name: 'UploadedFile',
  methods: {
    deleteFile (file) {
      this.$emit("delete-file", file);
    },
    downloadFile (event) {
      event.preventDefault()
      let url = event.target.href

      this.downloadKey += 1

      this.$nextTick().then(() => {
        this.$refs.downloader.downloadFile(url)
      })
    }
  }
}
</script>

<style scoped>
iframe {
    display: none;
}
</style>
