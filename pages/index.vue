<template>
  <section class="container">
    <div>
      <logo />
      <h1 class="title">
        nuxt-headless-cms-demo
      </h1>
      <h2 class="subtitle">
        My beautiful Nuxt.js project
      </h2>
      <div class="links">
        <div v-for="(post, index) in allPosts" :key="index">
          <nuxt-link :to="`/blog/${post.slug}`" class="button--grey">
            {{ post.title }}
          </nuxt-link>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import gql from 'graphql-tag'
import Logo from '~/components/Logo.vue'

export default {
  apollo: {
    allPosts: gql`
      {
        allPosts {
          title
          body
          slug
        }
      }
    `
  },
  components: {
    Logo
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
