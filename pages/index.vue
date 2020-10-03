<template>
  <div>
    <section class="hero is-primary is-fullheight">
      <div class="hero-video">
        <video id="bgvid" poster="assets/texture.png" playsinline autoplay muted loop>
          <source src="http://dl5.webmfiles.org/big-buck-bunny_trailer.webm" type="video/webm">
          <source
            src="http://video.blendertestbuilds.de/download.blender.org/peach/trailer_480p.mov"
            type="video/mp4"
          >
        </video>
      </div>
      <div class="hero-body">
        <div class="container">
          <h1 class="title">{{ page.title }}</h1>
          <h2 class="subtitle">{{ page.description }}</h2>
        </div>
      </div>
      <div class="hero-foot">
        <nav class="tabs is-large">
          <div class="container">
            <ul>
              <li>
                <a href="https://www.instagram.com/thepavlosp/" target="_blank">
                  <i class="fab fa-instagram" />
                </a>
              </li>
              <li>
                <a href="https://twitter.com/thepavlosp" target="_blank">
                  <i class="fab fa-twitter" />
                </a>
              </li>
              <li>
                <a href="https://www.linkedin.com/in/pavlospapaefstathiou/" target="_blank">
                  <i class="fab fa-linkedin-in" />
                </a>
              </li>
              <li>
                <a href="https://pavlosp.myportfolio.com/" target="_blank">
                  <i class="far fa-images" />
                </a>
              </li>
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
    const page = await $content('index')
      .fetch()
      .catch(() => {
        error({ statusCode: 404, message: 'Page not found' });
      });

    return {
      page
    };
  },

  data() {
    return {
      title: 'Pavlos Papaefstathiou'
    };
  },

  head() {
    return {
      title: this.title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Pavlos Papaefstathiou; homepage'
        }
      ]
    };
  }
};
</script>

<style>
.hero-video video {
  position: relative;
  left: auto;
  top: auto;
  transform: none;
  object-fit: cover;
}
</style>
