<template>
  <div>
    <section class="hero is-primary is-medium has-background">
      <div class="hero-body">
        <div class="container">
          <h1 class="title">
            {{ page.title }}
          </h1>
          <h2 class="subtitle">
            {{ page.description }}
          </h2>
        </div>
      </div>
      <div class="hero-foot">
        <nav class="tabs">
          <div class="container">
            <ul>
              <li><a href="https://www.instagram.com/thepavlosp/" target="_blank"><i class="fab fa-instagram" /></a></li>
              <li><a href="https://twitter.com/thepavlosp" target="_blank"><i class="fab fa-twitter" /></a></li>
              <li><a href="https://www.linkedin.com/in/pavlospapaefstathiou/" target="_blank"><i class="fab fa-linkedin-in" /></a></li>
              <li><a href="https://pavlosp.myportfolio.com/" target="_blank">Portfolio</a></li>
            </ul>
          </div>
        </nav>
      </div>
    </section>
    <section class="section">
      <div class="container">
        <div class="columns">
          <div class="column is-8 is-offset-2">
            <div class="content">
              <nuxt-content :document="page" />
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    const slug = params.slug || "index";
    const page = await $content(slug)
      .fetch()
      .catch(err => {
        error({ statusCode: 404, message: "Page not found" });
      });

    return {
      page
    };
  }
};
</script>

<style lang="sass">
.hero
  &.has-background
    background-image: url("~assets/texture.png")
    background-repeat: repeat

</style>
