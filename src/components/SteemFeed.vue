<template>
    <div class="steemfeed">
        <h1>Steem Feed</h1>
        <main v-for="post in posts" :key="post.id">
            <router-link :to="`${post.author}/${post.permlink}`">
                <h2>{{post.title}}</h2>
            </router-link>
         </main>
    </div>
</template>
    
<script>
    const dsteem = require('dsteem')
    export default {
        name: 'SteemFeed',
        data () {
            return {
                posts: null
            }
        },
        created () {
            const client = new dsteem.Client('https://api.steemit.com')
            client.database.getDiscussions('blog', { tag: 'sambillingham', limit: 20 })
            .then(result => {
                this.posts = result
            })
        }
    }
</script>