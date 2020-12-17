<template>
  <section>
    <div class="container is-fluid">
      <h2 class="title is-2">{{post.fields.title}}</h2>
      <hr>
      <div class="content" v-html="$md.render(post.fields.content)">
      </div>
    </div>
  </section>
</template>

<script>
import client from '~/plugins/contentful'
export default {
  asyncData({ params, error, payload }) {
    if(payload) return { post: payload }
    return client.getEntries({
      content_type: 'post',
      'fields.slug': params.slug,
    })
    .then(entries => {
      return { post: entries.items[0] }
    })
    .catch(e => console.log(e))
  },
  head() {
    return {
      title: this.post.fields.title
    }
  }
}
</script>

<style>
</style>
