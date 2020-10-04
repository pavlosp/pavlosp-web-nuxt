<template>
  <div>
    <section class="hero is-primary is-fullheight">
      <div class="hero-video">
        <video id="bgvid" poster="images/pavlosp-profile-still.jpg" playsinline autoplay muted loop>
          <source src="~assets/pavlosp-profile-video.webm" type="video/webm">
          <source src="~assets/pavlosp-profile-video-h264.mp4" type="video/mp4">
        </video>
      </div>
      <div class="hero-body">
        <div class="container">
          <h1 class="title">{{ page.title }}</h1>
          <h2 class="subtitle">{{ page.description }}</h2>
        </div>
      </div>
      <div class="hero-foot">
        <div class="arrow bounce has-text-centered">
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
      page,
    };
  },

  data() {
    return {
      title: 'Pavlos Papaefstathiou',
      vh: 0,
    };
  },

  mounted() {
    this.$nextTick(() => {
      // First we get the viewport height and we multiple it by 1% to get a value for a vh unit
      this.vh = window.innerHeight * 0.01;

      document.documentElement.style.setProperty('--vh', `${this.vh}px`);

      // eslint-disable-next-line no-console
      console.log('DEBUG: set vh to ', this.vh);

      window.addEventListener('resize', () => {
        // We execute the same script as before
        this.vh = window.innerHeight * 0.01;
        document.documentElement.style.setProperty('--vh', `${this.vh}px`);

        // eslint-disable-next-line no-console
        console.log('DEBUG: set vh to ', this.vh);
      });
    });
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
  object-fit: cover;
}

.hero-video {
  display: inline;
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

.hero .is-fullheight {
  height: 100vh; /* Fallback for browsers that do not support Custom Properties */
  height: calc(var(--vh, 1vh) * 100);
}
</style>
