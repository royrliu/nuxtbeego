{{{{raw}}}}
<template>
  <section class="container">
    <img src="~assets/img/logo.png" alt="Nuxt.js Logo" class="logo" />
    <h1 class="title">
      Tags
    </h1>
    <h2 class="info">
      {{ user.Username }}
    </h2>
    <nuxt-link class="button" to="/">
      Featured Tags
    </nuxt-link>
  </section>
</template>
{{{{/raw}}}}

<script>
import axios from '~/plugins/axios'

export default {
  name: 'id',
  layout: 'basicLayout',
  asyncData ({ params, error }) {
    return axios.get('/api/users/' + params.id)
      .then((res) => {
        return { user: res.data }
      })
      .catch((e) => {
        error({ statusCode: 404, message: 'Tag not found' })
      })
  },
  head () {
    return {
      title: `Tag: ${this.user.name}`
    }
  }
}
</script>

<style scoped>
.title
{
  margin-top: 30px;
}
.info
{
  font-weight: 300;
  color: #9aabb1;
  margin: 0;
  margin-top: 10px;
}
.button
{
  margin-top: 30px;
}
</style>
