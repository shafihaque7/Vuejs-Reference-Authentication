/**
* Created by vouill on 11/13/17.
*/

<template>
  <div>
    <loading v-if="loading"/>
    <div v-if="isAuthenticated">
      <!-- <feed-item v-for="(feed, index) in fakeFeed" :key="index" :feed="feed"/> -->
      <contact></contact>
    </div>
    <div v-if="!isAuthenticated && authStatus !== 'loading'">
      <h1>Welcome to DogeBook !</h1>
      <p>When meeting new doge friends is harder than ever, Dogebook closes the gap between all paws in the world</p>
      <login/>
    </div>
  </div>
</template>

<style>
  .home {
    display: flex;
    align-items: center;
    flex-direction: column;
  }
</style>

<script>
  import fakeFeed from './fakeFeed'
  import FeedItem from './feedItem.vue'
  import contact from './contact.vue'
  import { mapGetters } from 'vuex'
  import Login from 'components/login'

  export default {
    components: {
      Login,
      FeedItem,
      contact
    },
    name: 'home',
    computed: {
      ...mapGetters(['isAuthenticated', 'authStatus']),
      loading: function () {
        return this.authStatus === 'loading' && !this.isAuthenticated
      }
    },
    data () {
      return ({ fakeFeed })
    },
  }
</script>
