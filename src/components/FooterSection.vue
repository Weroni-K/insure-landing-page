<template>
  <div id="footer-section">
    <div class="footer-content">
      <div class="upper-part">
        <div class="logo">
          <img src="/src/assets/logo.svg" alt="Insure logo" class="insure-logo" />
        </div>
        <div class="links-social">
          <a
            v-for="(social, socialIndex) in linksSocial"
            :key="socialIndex"
            :href="social.url"
            class="link-social"
            target="_blank"
          >
            <img :src="social.logo" alt="Social media logo" class="icon-social" />
          </a>
        </div>
      </div>
      <div class="links-container">
        <div v-for="(column, titleIndex) in footerColumns" :key="titleIndex" class="links-column">
          <h3>{{ column.title }}</h3>
          <ul>
            <li v-for="(link, linkIndex) in column.links" :key="linkIndex">
              <a :href="link.url"
                ><p>{{ link.text }}</p></a
              >
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import FacebookIcon from './../assets/icons/icon-facebook.svg'
import TwitterIcon from './../assets/icons/icon-twitter.svg'
import PinterestIcon from './../assets/icons/icon-pinterest.svg'
import InstagramIcon from './../assets/icons/icon-instagram.svg'

const footerColumns = ref([
  {
    title: 'Our company',
    links: [
      { text: 'How we work', url: './' },
      { text: 'Why Insure?', url: './' },
      { text: 'View plans', url: './' },
      { text: 'Reviews', url: './' },
    ],
  },
  {
    title: 'Help me',
    links: [
      { text: 'FAQ', url: './' },
      { text: 'Terms of use', url: './' },
      { text: 'Privacy policy', url: './' },
      { text: 'Cookies', url: './' },
    ],
  },
  {
    title: 'Contact',
    links: [
      { text: 'Sales', url: './' },
      { text: 'Support', url: './' },
      { text: 'Live chat', url: './' },
    ],
  },
  {
    title: 'Others',
    links: [
      { text: 'Careers', url: './' },
      { text: 'Press', url: './' },
      { text: 'Licenses', url: './' },
    ],
  },
])

const linksSocial = ref([
  { logo: FacebookIcon, url: 'https://facebook.com' },
  { logo: TwitterIcon, url: 'https://twitter.com' },
  { logo: PinterestIcon, url: 'https://pinterest.com' },
  { logo: InstagramIcon, url: 'https://instagram.com' },
])
</script>

<style scoped>
#footer-section {
  color: var(--color-neutral-dark-greyish-violet);
  background: var(--color-neutral-light-grey) url(../assets/images/bg-pattern-footer-desktop.svg)
    no-repeat left top / 36%;
}

.footer-content {
  max-width: 1110px;
  margin: 0 auto;
  padding: 2rem 0;
}

.upper-part {
  display: flex;
  justify-content: space-between;
  border-bottom: 1px solid hsla(273, 4%, 51%, 0.25);
  padding: 2rem 0;
}

.links-social {
  display: flex;
  gap: 1rem;
}
.icon-social:hover {
  filter: hue-rotate(-17deg) saturate(650%) brightness(40%);
}

.links-container {
  columns: 4;
  text-transform: uppercase;
  padding: 3rem 0 1.5rem 0;
}

h3 {
  font-size: 14px;
  padding-bottom: 1.5rem;
}
p {
  color: var(--color-primary-dark-violet);
  font-weight: var(--font-weight-700);
  font-size: 14px;
  padding-bottom: 0.5rem;
}

a:hover {
  text-decoration: underline;
}

@media (max-width: 1180px) {
  .footer-content {
    margin: 0 24px;
  }
}

@media (max-width: 560px) {
  #footer-section {
    color: var(--color-neutral-dark-greyish-violet);
    background: var(--color-neutral-light-grey) url(../assets/images/bg-pattern-footer-mobile.svg)
      no-repeat top / contain;
  }
  .upper-part {
    margin-top: 2rem;
    flex-direction: column;
    align-items: center;
    gap: 2rem;
  }
  .links-container {
    columns: 1;
    text-align: center;
    padding: 2rem 0 1.5rem 0;
  }
  .links-column {
    margin-bottom: 2rem;
  }
  h3 {
    padding-bottom: 1rem;
  }
}
</style>
