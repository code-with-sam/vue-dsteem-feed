<template>
    <div class="steemfeed">
        <h1>Steem Feed</h1>
    </div>
</template>
    
<script>
    const dsteem = require('dsteem')
    export default {
        name: 'SteemFeed',
        created () {
            const client = new dsteem.Client('https://api.steemit.com')
            client.database.getDiscussions('blog', { tag: 'sambillingham', limit: 20 })
            .then(result => {
                console.log(result)
            })
        }
    }
</script>