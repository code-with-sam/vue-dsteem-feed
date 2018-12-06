<template>
  <div>
    <h1>{{ title }}</h1>
    <main>{{ content }}</main>
  </div>
</template>

<script>
const dsteem = require('dsteem')

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
        this.content = response.body
    })
  }
}
</script>