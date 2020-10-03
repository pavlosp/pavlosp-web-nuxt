<template>
  <div>
    <section class="hero is-primary is-fullheight">
      <div class="hero-video">
        <video id="bgvid" poster="~assets/texture.png" playsinline autoplay muted loop>
          <source
            src="~assets/pavlosp-background-h264.mp4"
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
        <div class="arrow bounce">
          <p class="fas fa-chevron-down fa-2x" />
        </div>
      </div>
    </section>
    <section class="section">
      <div class="container">
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

.hero-video {
  display: inline;
}

.arrow {
  text-align: center;
}
.bounce {
  -moz-animation: bounce 2s infinite;
  -webkit-animation: bounce 2s infinite;
  animation: bounce 2s infinite;
}

@keyframes bounce {
  0%, 20%, 50%, 80%, 100% {
    transform: translateY(0);
  }
  40% {
    transform: translateY(-30px);
  }
  60% {
    transform: translateY(-15px);
  }
}
</style>
