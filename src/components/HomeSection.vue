<template>
  <div id="home-section">
    <div class="content-container">
      <div class="text">
        <h1>Humanizing your insurance.</h1>
        <p>
          Get your life insurance coverage easier and faster. We blend our expertise and technology
          to help you find the plan that’s right for you. Ensure you and your loved ones are
          protected.
        </p>
        <a href="./">
          <button class="view-plans-button">View Plans</button>
        </a>
      </div>
      <img :src="introImage" class="intro-illustration" alt="Intro Image" />
    </div>
  </div>
</template>

<script setup>
import { computed, reactive, onMounted, onBeforeUnmount } from 'vue'
import IntroImageDesktop from '../assets/images/image-intro-desktop.jpg'
import IntroImageMobile from '../assets/images/image-intro-mobile.jpg'
const introImage = computed(() => {
  return isDesktop.value ? IntroImageDesktop : IntroImageMobile
})

const windowSize = reactive({
  width: window.innerWidth,
  height: window.innerHeight,
})

const updateWindowSize = () => {
  windowSize.width = window.innerWidth
  windowSize.height = window.innerHeight
}

onMounted(() => {
  window.addEventListener('resize', updateWindowSize)
})

onBeforeUnmount(() => {
  window.removeEventListener('resize', updateWindowSize)
})

const isDesktop = computed(() => {
  return windowSize.width >= 1180
})
</script>
<style scoped>
#home-section {
  position: relative;
  padding: 6.5rem 0 0 0;
  margin: 0 auto;
}

#home-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 66%;
  background-color: var(--color-primary-dark-violet);
  z-index: -1;
}

.content-container {
  max-width: 1110px;
  margin: 0 auto;
  display: flex;
  gap: 2rem;
  justify-content: space-between;
  position: relative;
}

.content-container::before,
.content-container::after {
  content: '';
  position: absolute;
  height: 1px;
  width: 9.5%;
}

.content-container::before {
  top: 0;
  left: 0;
  background-color: var(--color-neutral-light-grey);
}

.content-container::after {
  bottom: 0;
  left: 0;
  background-color: var(--color-neutral-dark-greyish-violet);
}

.text {
  padding-top: 4rem;
  display: flex;
  flex-direction: column;
  gap: 1.6rem;
  z-index: 2;
}

h1 {
  color: var(--color-neutral-light-grey);
  overflow-wrap: break-word;
}

p {
  color: var(--color-neutral-light-grey);
}

.view-plans-button {
  padding: 8px 2rem;
  color: var(--color-neutral-light-grey);
  background: transparent;
  border: 2px solid var(--color-neutral-light-grey);
  font-weight: var(--font-weight-700);
  text-transform: uppercase;
}

.view-plans-button:hover {
  cursor: pointer;
  color: var(--color-neutral-very-dark-violet);
  background-color: var(--color-neutral-light-grey);
}

.intro-illustration {
  margin-bottom: 9.5rem;
}

@media (max-width: 1180px) {
  #home-section {
    padding-left: 24px;
  }
  #home-section::before {
    height: 81%;
  }
  .intro-illustration {
    min-height: 540px;
    margin-bottom: 9.5rem;
    align-self: baseline;
  }
  h1 {
    font-size: 46px;
  }
}
@media (max-width: 768px) {
  #home-section {
    padding: 0;
  }
  #home-section::before {
    height: 88%;
  }
  .content-container {
    flex-direction: column-reverse;
    padding-bottom: 10rem;
  }
  .intro-illustration {
    min-height: auto;
    margin: auto;
    margin-bottom: 4rem;
  }
  .content-container::before {
    display: none;
  }
  .content-container::after {
    left: calc(50% - 1rem);
    width: 2rem;
  }
  .text {
    padding-top: 0;
    align-items: center;
    text-align: center;
    margin-inline: 24px;
    gap: 1rem;
  }
  .view-plans-button {
    margin: 1rem 0 4rem 0;
  }
  h1 {
    line-height: 1.1;
  }
}

@media (max-width: 375px) {
  .intro-illustration {
    position: relative;
    margin-bottom: 0;
  }

  .content-container {
    gap: 0;
  }

  .text {
    position: relative;
    padding-top: 6rem;
  }

  h1 {
    z-index: 2;
  }

  .text::after {
    content: '';
    position: absolute;
    height: 10rem;
    max-width: 100%;
    aspect-ratio: 1;
    background: url('../assets/images/bg-pattern-intro-left-mobile.svg') no-repeat left top;
    z-index: 1;
    top: 0;
    left: -24px;
  }
}
</style>
