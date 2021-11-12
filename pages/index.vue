<template>
  <div>
    <li v-for="link of links" :key="link.slug">
      <NuxtLink :to="link.slug">{{ link.title }}</NuxtLink>
    </li>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const links = await $content("links").fetch()

    return {
      links,
    };
  },
  head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  },
}
</script>
