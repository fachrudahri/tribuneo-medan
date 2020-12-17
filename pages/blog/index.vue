<template>
  <section>
    <div class="container is-fluid">
      <h3 class="mb-4 title is-4">Latest Posts</h3>
      <div class="columns is-multiline">
        <div v-for="(post, index) in posts" :key="index" class="column is-3">
          <div class="card">
            <div class="card-image">
              <figure class="image is-4by3">
                <img
                  src="https://bulma.io/images/placeholders/1280x960.png"
                  alt="Placeholder image"
                />
              </figure>
            </div>
            <div class="card-content">
              <p class="title is-5">
                {{ post.fields.title }}
              </p>
              <div class="buttons"><nuxt-link :to="`blog/${post.fields.slug}`" class="button is-primary is-light">Read More</nuxt-link>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import client from '~/plugins/contentful'
export default {
  asyncData() {
    return client
      .getEntries({
        content_type: 'post',
      })
      .then((entries) => {
        return { posts: entries.items }
      })
      .catch((e) => console.log(e))
  },
  head: {
    title: 'Latest Posts',
  },
}
</script>

