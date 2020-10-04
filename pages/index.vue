<template>
  <div>
    <section class="hero is-primary is-fullheight vh-fix">
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
  object-fit: cover;
}

.hero-video {
  display: flex;
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

/** 
 * iPhone 6-8 with portrait orientation.
 */
@media all and (device-width: 375px) and (device-height: 667px) and (orientation:portrait){
  .hero.is-fullheight.vh-fix {
    min-height: 550px;
  }
}

/** 
 * iPhone 8 Plus with portrait orientation.
 */
@media all and (device-width: 414px) and (device-height: 736px) and (orientation:portrait){
  .hero.is-fullheight.vh-fix {
    min-height: 619px;
  }
}

/** 
 * iPhone Xr / Xs Max / 11 / 11 Pro Max with portrait orientation.
 */
@media all and (device-width: 414px) and (device-height: 896px) and (orientation:portrait){
  .hero.is-fullheight.vh-fix {
    min-height: 779px;
  }
}

/** 
 * iPhone Xs / 11 Pro with portrait orientation.
 */
@media all and (device-width: 375px) and (device-height: 812px) and (orientation:portrait){
  .hero.is-fullheight.vh-fix {
    min-height: 695px;
  }
}

/** 
 * iPad / iPad 2 / ... with portrait orientation.
 */
@media all and (device-width: 768px) and (device-height: 1024px) and (orientation:portrait){
  .hero.is-fullheight.vh-fix {
    min-height: 899px;
  }
}

/** 
 * iPad / iPad 2 / ... with landscape orientation.
 */
@media all and (device-width: 768px) and (device-height: 1024px) and (orientation:landscape){
  .hero.is-fullheight.vh-fix {
    min-height: 643px;
  }
}

/** 
 * iPad Pro 12.9 all gen with portrait orientation.
 */
@media all and (device-width: 1024px) and (device-height: 1366px) and (orientation:portrait){
  .hero.is-fullheight.vh-fix {
    min-height: 1241px;
  }
}

/** 
 * iPad Pro 12.9 all gen with landscape orientation.
 */
@media all and (device-width: 1024px) and (device-height: 1366px) and (orientation:landscape){
  .hero.is-fullheight.vh-fix {
    min-height: 899px;
  }
}

/** 
 * iPad Pro 2nd gen 10.5 / iPad Air 3rd Gen with portrait orientation.
 */
@media all and (device-width: 834px) and (device-height: 1112px) and (orientation:portrait){
  .hero.is-fullheight.vh-fix {
    min-height: 987px;
  }
}

/** 
 * iPad Pro 2nd gen 10.5 / iPad Air 3rd Gen with landscape orientation.
 */
@media all and (device-width: 834px) and (device-height: 1112px) and (orientation:landscape){
  .hero.is-fullheight.vh-fix {
    min-height: 709px;
  }
}

/** 
 * iPad Pro 3rd Gen 11'' with portrait orientation.
 */
@media all and (device-width: 834px) and (device-height: 1194px) and (orientation:portrait){
  .hero.is-fullheight.vh-fix {
    min-height: 1069px;
  }
}

/** 
 * iPad Pro 3rd Gen 11'' with landscape orientation.
 */
@media all and (device-width: 834px) and (device-height: 1194px) and (orientation:landscape){
  .hero.is-fullheight.vh-fix {
    min-height: 709px;
  }
}

/** 
 * iPad 7th gen with portrait orientation.
 */
@media all and (device-width: 810px) and (device-height: 1080px) and (orientation:portrait){
  .hero.is-fullheight.vh-fix {
    min-height: 955px;
  }
}

/** 
 * iPad 7th gen with landscape orientation.
 */
@media all and (device-width: 810px) and (device-height: 1080px) and (orientation:landscape){
  .hero.is-fullheight.vh-fix {
    min-height: 685px;
  }
}

</style>
