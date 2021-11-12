<template>
  <div>
    <h1>{{settings.title}}</h1>
    <li v-for="link of links" :key="link.slug">
      <a :href="link.link">{{ link.title }}</a>
      <p>{{link.description}}</p>
    </li>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const links = await $content("links").fetch()
    const settings = await $content("settings").fetch()

    return {
      links,
      settings
    };
  },
  head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  },
}
</script>
