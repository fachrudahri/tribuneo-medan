<template>
  <div>
    <section class="has-text-centered pt-5 pb-6">
      <div class="columns is-multiline">
        <div class="column is-full">
          <h1 class="title is-1 has-text-link-dark">Welcome Everyone 😉</h1>
        </div>
        <div class="column is-half is-offset-one-quarter">
          <p class="has-text-grey">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Ipsam a vel
            ipsa ut, ad repellendus voluptatem accusamus, veritatis assumenda
            facilis neque saepe, incidunt illum praesentium corporis iusto rem
            quo quasi.
          </p>
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
                    <img :src="asset[index].fields.file.url" alt="Placeholder image">
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
