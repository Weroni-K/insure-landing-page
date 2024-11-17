<template>
  <main>
    <HeaderSection />
    <div class="backgroundsvgs">
      <HomeSection />
      <FeaturesSection />
    </div>
    <FindOutSection />
    <FooterSection />
  </main>
</template>

<script setup>
import HeaderSection from './components/HeaderSection.vue'
import HomeSection from './components/HomeSection.vue'
import FeaturesSection from './components/FeaturesSection.vue'
import FindOutSection from './components/FindOutSection.vue'
import FooterSection from './components/FooterSection.vue'
</script>

<style scoped>
.backgroundsvgs {
  position: relative;
}

.backgroundsvgs::before {
  content: '';
  position: absolute;
  top: -5rem;
  right: 0;
  height: 36rem;
  aspect-ratio: 1;
  background: url('./assets/images/bg-pattern-intro-right-desktop.svg') no-repeat right center;
  background-size: contain;
  z-index: 1;
  clip-path: inset(5rem 0 0 0);
}

.backgroundsvgs::after {
  content: '';
  position: absolute;
  top: 26.5rem;
  height: 32rem;
  aspect-ratio: 1;
  background: url('./assets/images/bg-pattern-intro-left-desktop.svg') no-repeat left center;
  background-size: contain;
  z-index: 1;
}

@media (max-width: 768px) {
  .backgroundsvgs::before {
    clip-path: none;
    top: 45.8rem;
    height: 30rem;
    background: url('./assets/images/bg-pattern-intro-right-mobile.svg') no-repeat right center;
  }

  .backgroundsvgs::after {
    top: -1.8rem;
    height: 14rem;
    background: url('./assets/images/bg-pattern-intro-left-mobile.svg') no-repeat left center;
  }
}

@media (max-width: 375px) {
  .backgroundsvgs::after {
    display: none;
  }
}
</style>
