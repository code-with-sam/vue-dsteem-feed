<template>
  <div>
    <h1>{{ title }}</h1>
    <main v-html="content"></main>
  </div>
</template>

<script>
const dsteem = require('dsteem')
import marked from 'marked'

export default {
  name: 'SteemPost',
  data () {
    return {
        title: null,
        content: null
    }
  },
  created () {
    const client = new dsteem.Client('https://api.steemit.com')
    client.call('condenser_api', 'get_content', [this.$route.params.username, this.$route.params.permlink])
    .then(response => {
        this.title = response.title
        this.content = marked(response.body, { sanitize: true })
    })
  }
}
</script>

<style scoped>
main {
  max-width: 700px;
  margin: 0 auto;
  text-align: left;
}
* >>> img {
  max-width: 100%;
}
</style>