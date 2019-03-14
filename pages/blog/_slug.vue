<template>
  <div v-if="post">
    <h1>{{ post.title }}</h1>
    <div>
      {{ post.body }}
    </div>
    <nuxt-link :to="{ name: 'index' }" class="button--green">Home</nuxt-link>
  </div>
</template>

<script>
import gql from 'graphql-tag'
export default {
  apollo: {
    post: {
      query: gql`
        query Post($slug: String!) {
          post(filter: { slug: { matches: { pattern: $slug } } }) {
            title
            body
          }
        }
      `,
      prefetch({ route }) {
        return {
          slug: route.params.slug
        }
      },
      variables() {
        return {
          slug: this.$route.params.slug
        }
      }
    }
  }
}
</script>
