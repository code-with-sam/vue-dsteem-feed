<template>
  <div>
    <h1>STEEM Post</h1> 
  </div>
</template>

<script>
const dsteem = require('dsteem')

export default {
  name: 'SteemPost',
  data () {
    return {
    }
  },
  created () {
    const client = new dsteem.Client('https://api.steemit.com')
    client.call('condenser_api', 'get_content', [this.$route.params.username, this.$route.params.permlink])
    .then(response => {
        console.log(response)
    })
  }
}
</script>
