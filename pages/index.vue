<template>
  <div>
    <section class="container pt-5 pb-6">
      <div class="container is-fluid">
        <div class="columns is-vcentered is-multiline">
          <div class="column is-6">
            <h1 class="title is-1 has-text-link-dark has-text-weight-bold">BETTER LIVING THROUGH TRIBUNEO MEDAN</h1>
              <p class="subtitle is-6 has-text-grey pt-2">
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Ipsa repudiandae consequatur sapiente omnis, totam maiores. Omnis saepe eos deserunt ut est voluptates dolorum, ex fugit tenetur consequatur.
              </p>
          </div>
          <div class="column is-6">
            <figure class="image is-square">
              <img src="@/assets/scene.png">
            </figure>
          </div>
        </div>
      </div>
    </section>
    <section class="container mb-5 pt-6 pb-6">
        <h3 class="title is-3 has-text-centered">Team</h3>
      <div class="container is-fluid level">
        <div class="level-item has-text-centered">
          <div class="mt-5">
            <p class="heading">Piyan</p>
            <figure class="image is-128x128">
              <img class="is-rounded" src="https://bulma.io/images/placeholders/128x128.png">
            </figure>
          </div>
        </div>
        <div class="level-item has-text-centered">
          <div class="mt-5">
            <p class="heading">Fauzi</p>
            <figure class="image is-128x128">
              <img class="is-rounded" src="https://bulma.io/images/placeholders/128x128.png">
            </figure>
          </div>
        </div>
        <div class="level-item has-text-centered">
          <div class="mt-5">
            <p class="heading">Irul</p>
            <figure class="image is-128x128">
              <img class="is-rounded" src="https://bulma.io/images/placeholders/128x128.png">
            </figure>
          </div>
        </div>
        <div class="level-item has-text-centered">
          <div class="mt-5">
            <p class="heading">Isfan</p>
            <figure class="image is-128x128">
              <img class="is-rounded" src="https://bulma.io/images/placeholders/128x128.png">
            </figure>
          </div>
        </div>
      </div>
    </section>
    <section class="pt-6 pb-6 has-background-link">
      <div class="container">
        <div class="container is-fluid">
          <h3 class="title is-3 has-text-centered has-text-light">New Posts</h3>
          <div class="columns is-multiline">
            <div v-for="(post, index) in entries" :key="index" class="column is-4">
              <div v-if="index < 3">
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
                    <p class="title is-5 no-mb">
                      {{ post.fields.title }}
                    </p>
                    <small class="has-text-grey">{{ post.fields.date }}</small>
                    <div class="buttons mt-3">
                      <nuxt-link
                        :to="`blog/${post.fields.slug}`"
                        class="button is-link is-light"
                        >Read More</nuxt-link
                      >
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
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
    title: 'Home Tribun-eo Medan',
  },
}
</script>

<style>
</style>
