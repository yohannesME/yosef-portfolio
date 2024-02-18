<template>
  <div>
    <h2 class="heading" id="portfolio">My <span>Portfolio</span></h2>
    <div class="portfolio">
      <div class="box-container">
        <div class="box" v-for="project in portfolio" :key="project.title">
          <img :src="project.img" alt="" />
          <div class="content">
            <h3>{{ project.title }}</h3>
            <span class="highlight">{{ project.description }}</span><br />
            <span class="span">{{ project.techStack.toString() }}</span>
            <a v-show="project.repo" :href="project.repo">
              <i class="fab fa-github"></i>
            </a>
            <a v-show="project.link" :href="project.link" target="_blank">
              <i class="fas fa-link"></i>
            </a>
          </div>
        </div>
        <a
          class="btn cv"
          href="https://docs.google.com/presentation/d/1WnK-4pYV2jrD1bWB3T9-kic-BT2YzZkrYcaG1hkmkX0/edit?usp=sharing"
          target="_blank"
          type="button"
        >
          Slide Deck
        </a>

        <div class="video-container">
          <iframe
            width="560"
            height="315"
            :src="getYouTubeEmbedUrl('rKU8p3ft5ys')"
            frameborder="0"
            allowfullscreen
          ></iframe>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { portfolio } from "@/assets/data";

export default {
  data() {
    return {
      portfolio,
    };
  },
  methods: {
    getYouTubeEmbedUrl(videoId) {
      return `https://www.youtube.com/embed/${videoId}`;
    },
  },
};
</script>

<style scoped>
.portfolio .box-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(27rem, 1fr));
  gap: 2rem;

  padding: 3rem;
  max-width: 92%;
  margin: 1rem auto;
}

.portfolio .box-container .box {
  height: 30rem;
  border-radius: 0.5rem;
  overflow: hidden;
  /* box-shadow: var(--box-shadow); */
  box-shadow: var(--box-shadow-inset);
  position: relative;
  border: 1rem solid transparent;
  transition: all 5000s ease-out;
}

.portfolio .box-container .box:hover {
  box-shadow: var(--box-shadow);
  transition: all 5s;
}

.portfolio .box-container .box img {
  height: 100%;
  width: 100%;
  object-fit: contain;
}

.portfolio .box-container .box .content {
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  background: var(--bg-color);
  display: grid;
  place-items: center;
  transform: scale(0);
}

.portfolio .box-container .box:hover .content {
  transform: scale(1);
  /* box-shadow: var(--box-shadow);
    transition:all 5s; */
  /* box-shadow: var(--box-shadow); */
}

.portfolio .box-container .box .content h3 {
  font-size: 2.5rem;
  color: var(--black);
  text-transform: uppercase;
  transform: translateY(-5rem);
  opacity: 0;
  transition-delay: 0.3s;
}
.portfolio .box-container .box .content a {
  font-size: 2.5rem;
  display: inline;
}

.portfolio .box-container .box:hover .content h3 {
  transform: translateY(0rem);
  opacity: 1;
}

.portfolio .box-container {
  /* existing styles */

  /* Add the following styles to create a grid layout */
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(27rem, 1fr));
  gap: 2rem;

}

.video-container {
  /* Add the following styles to make the video container responsive */
  position: relative;
  width: 100%;
    

}

.video-container video {
  /* Add the following styles to make the video fill the container */
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

</style>
