<template>
  <div id="features-section">
    <div class="features-title">
      <h1>We're different</h1>
    </div>
    <div class="features-cards">
      <div v-for="(card, index) in featuresCard" :key="index" class="features-card">
        <img :src="card.img" alt="Features image" class="features-img" />
        <h2>{{ card.title }}</h2>
        <p>{{ card.description }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import SnappyProcessImg from './../assets/icons/icon-snappy-process.svg'
import AffordablePricessImg from './../assets/icons/icon-affordable-prices.svg'
import PeopleFirstImg from './../assets/icons/icon-people-first.svg'

const featuresCard = ref([
  {
    title: 'Snappy Process',
    description:
      'Our application process can be completed in minutes, not hours. Don’t get stuck filling in tedious forms.',
    img: SnappyProcessImg,
  },
  {
    title: 'Affordable Prices',
    description:
      'We don’t want you worrying about high monthly costs. Our prices may be low, but we still offer the best coverage possible.',
    img: AffordablePricessImg,
  },
  {
    title: 'People First',
    description:
      'Our plans aren’t full of conditions and clauses to prevent payouts. We make sure you’re covered when you need it.',
    img: PeopleFirstImg,
  },
])
</script>

<style scoped>
#features-section {
  max-width: 1110px;
  margin: 0 auto;
  padding: 2rem 0;
}

.features-title {
  padding: 4rem 0;
}

.features-cards {
  columns: 3;
  padding: 2rem 0;
  gap: 2rem;
}

h2 {
  margin: 2rem 0 1.5rem 0;
}

p {
  color: var(--color-neutral-dark-greyish-violet);
  line-height: 1.6;
}

@media (max-width: 1180px) {
  #features-section {
    margin: 0 24px;
  }
  h1 {
    font-size: 46px;
  }
}

@media (max-width: 768px) {
  h1 {
    text-align: center;
  }
  .features-cards {
    padding: 1.5rem 0;
    display: flex;
    flex-direction: column;
    gap: 3.5rem;
  }
  .features-card {
    justify-items: center;
    text-align: center;
  }
}
</style>
