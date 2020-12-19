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
    <section class="pt-6 pb-6 has-background-dark">
      <div class="container">
        <div class="container is-fluid">
          <div class="columns is-multiline">
            <div v-for="(post, index) in posts" :key="index" class="column is-4">
              <div v-if="index < 3">
                <div class="card">
                  <div class="card-content">
                    <p class="title is-5">
                      {{ post.fields.title }}
                    </p>
                    <div class="buttons">
                      <nuxt-link
                        :to="`blog/${post.fields.slug}`"
                        class="button is-primary is-light"
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
    title: 'Home Tribun-eo Medan',
  },
}
</script>

<style>
</style>
