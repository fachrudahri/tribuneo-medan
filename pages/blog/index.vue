<template>
  <section>
    <div class="container">
      <div class="container is-fluid">
      <h3 class="mb-4 title is-4">Latest Posts</h3>
      <div class="columns is-multiline">
        <div v-for="(post, index) in entries" :key="index" class="column is-3">
          <div class="card">
            <div class="card-image">
              <figure class="image is-1by1">
                <div v-for="(ast, index) in asset" :key="index">
                  <div v-if="ast.fields.title == post.fields.title">
                    <img :src="ast.fields.file.url" alt="Placeholder image">
                  </div>
                </div>
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
    </div>
  </section>
</template>

<script>
import client from '~/plugins/contentful'
export default {
  async asyncData() {
    const asset = await client.getAssets()
      .then((asset) =>{ return { assets: asset.items }
      })
      .catch((e) => console.log(e))

    const entries = await client.getEntries({content_type: 'post'})
      .then((entries) => {
        return { posts: entries.items }
      })
      .catch((e) => console.log(e))
      return {
        asset: asset.assets,
        entries: entries.posts
      }
  },
  head: {
    title: 'Latest Posts',
  },
}
</script>

