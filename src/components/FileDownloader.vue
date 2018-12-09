<template>
  <iframe v-bind:src="source"></iframe>
</template>

<script>
export default {
  data () {
    return {
      source: ''
    }
  },
  methods: {
    downloadFile (source) {
      this.$set(this, 'source', source)
    }
  }
}
</script>
