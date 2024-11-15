<template>
  <div id="header-section">
    <div class="navbar">
      <div class="logo">
        <img src="/src/assets/logo.svg" alt="Insure logo" class="insure-logo" />
      </div>

      <div class="nav-links" :class="{ active: isMenuOpen }" v-if="windowWidth > 768 || isMenuOpen">
        <div v-for="(link, index) in menuLinks" :key="index" class="nav-link">
          <a :href="link.url">{{ link.text }}</a>
        </div>
        <button class="view-plans-button">View Plans</button>
      </div>

      <button
        class="burger"
        @click="toggleMenu"
        aria-label="Toggle menu"
        v-if="windowWidth <= 768"
        :class="{ active: isMenuOpen }"
      >
        <span class="line-top"></span>
        <span class="line-mid"></span>
        <span class="line-bottom"></span>
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const menuLinks = ref([
  { text: 'How We Work', url: './' },
  { text: 'Blog', url: './' },
  { text: 'Account', url: './' },
])

const isMenuOpen = ref(false)
const windowWidth = ref(window.innerWidth)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
  // Disable/enable scrolling on the body
  if (isMenuOpen.value) {
    document.body.style.overflow = 'hidden' // Disable scroll
  } else {
    document.body.style.overflow = '' // Re-enable scroll
  }
}

const handleResize = () => {
  windowWidth.value = window.innerWidth
  if (windowWidth.value > 768) {
    isMenuOpen.value = false
  }
}

onMounted(() => {
  window.addEventListener('resize', handleResize)
})

onUnmounted(() => {
  window.removeEventListener('resize', handleResize)
})
</script>

<style scoped>
#header-section {
  max-width: 1110px;
  margin: 0 auto;
  padding: 2rem 0;
}

.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem 24px;
  height: 3rem;
}

.no-scroll {
  overflow: hidden;
}

.nav-links {
  display: flex;
  list-style-type: none;
  gap: 2rem;
  margin: 0;
  padding: 0;
  text-transform: uppercase;
  align-items: center;
  color: var(--color-neutral-dark-greyish-violet);
  font-weight: var(--font-weight-700);
  a:hover {
    color: var(--color-neutral-very-dark-violet);
  }
}

.view-plans-button {
  text-transform: uppercase;
  border: 2px solid var(--color-neutral-very-dark-violet);
  background: transparent;
  color: var(--color-neutral-very-dark-violet);
  font-weight: var(--font-weight-700);
  padding: 10px 2rem;
}

.view-plans-button:hover {
  cursor: pointer;
  background-color: var(--color-neutral-very-dark-violet);
  color: var(--color-neutral-light-grey);
}

.burger {
  display: none;
  background: transparent;
  border: 2px solid var(--color-neutral-very-dark-violet);
  cursor: pointer;
  flex-direction: column;
  padding: 8px 4px;
  width: 32px;
  height: 32px;

  span {
    width: 18px;
    height: 2px;
    margin: auto;
    background: var(--color-neutral-very-dark-violet);
    transition: all 0.4s ease;
  }

  .line-top {
    transform: translateY(-2px);
  }

  .line-bottom {
    transform: translateY(2px);
  }

  &.active {
    .line-top {
      transform: translateY(4px) rotate(45deg);
    }
    .line-mid {
      transform: translateX(-6px) rotate(360deg);
      opacity: 0;
    }
    .line-bottom {
      transform: translateY(-4px) rotate(-45deg);
    }
  }
}
@media (max-width: 768px) {
  #header-section {
    padding: 1rem 0.5rem;
  }

  .nav-links {
    display: none;
    height: calc(100vh - 5rem);
    width: 100%;
    margin: 0;
    left: 0;
    top: 5rem;
    background: var(--color-neutral-very-dark-violet)
      url(../assets/images/bg-pattern-mobile-nav.svg) no-repeat bottom / contain;
    color: var(--color-neutral-light-grey);
    font-size: 20px;
    font-weight: var(--font-weight-400);
    a:hover {
      color: var(--color-neutral-dark-greyish-violet);
    }
  }

  .nav-links.active {
    padding-top: 3rem;
    position: absolute;
    display: flex;
    flex-direction: column;
    gap: 2rem;
  }

  .view-plans-button {
    border: 2px solid var(--color-neutral-light-grey);
    color: var(--color-neutral-light-grey);
    font-weight: var(--font-weight-400);
    width: calc(100% - 48px);
  }

  .view-plans-button:hover {
    background-color: var(--color-neutral-light-grey);
    color: var(--color-neutral-very-dark-violet);
  }

  .burger {
    display: flex;
    position: absolute;
    right: 24px;
  }
}
</style>
