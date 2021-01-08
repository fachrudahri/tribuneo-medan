<template>
  <div>
    <section class="pb-6 hero-background">
      <div class="container">
        <div class="container is-fluid columns is-vcentered is-multiline is-centered hero-padding">
          <div class="column is-6">
            <h1 class="title is-1 has-text-white has-text-weight-bold">TRIBUN EO MEDAN</h1>
              <p class="subtitle has-text-justified is-6 has-text-white pt-2">
                Menjadi kelompok usaha penerbitan surat kabar, media online, dan percetakan daerah terbesar dan tersebar di Indonesia, melalui penyediaan informasi terpercaya untuk memberikan spirit baru dan mendorong terciptanya demokratisasi di daerah dengan menjalankan bisnis yang beretika, efisien, dan menguntungkan.
              </p>
          </div>
          <div class="column is-6">
            <figure class="has-text-centered">
              <img src="@/assets/Tribun-hero.png">
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
            <p class="heading">Vian</p>
            <figure class="image is-128x128">
              <img class="is-rounded" src="@/assets/vian.png">
            </figure>
          </div>
        </div>
        <div class="level-item has-text-centered">
          <div class="mt-5">
            <p class="heading">Fauzi</p>
            <figure class="image is-128x128">
              <img class="is-rounded" src="@/assets/fauzi.png">
            </figure>
          </div>
        </div>
        <div class="level-item has-text-centered">
          <div class="mt-5">
            <p class="heading">Irul</p>
            <figure class="image is-128x128">
              <img class="is-rounded" src="@/assets/irul.png">
            </figure>
          </div>
        </div>
        <div class="level-item has-text-centered">
          <div class="mt-5">
            <p class="heading">Isfan</p>
            <figure class="image is-128x128">
              <img class="is-rounded" src="@/assets/isfan.png">
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
