<template>
  <div id="find-out-section">
    <h2>Find out more<br />about how we work</h2>
    <button class="find-out-button">How we work</button>
  </div>
</template>

<script setup></script>

<style scoped>
#find-out-section {
  max-width: 1110px;
  margin: 6rem auto 9rem auto;
  padding: 4rem 6rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: var(--color-neutral-light-grey);
  background: var(--color-primary-dark-violet)
    url(../assets/images/bg-pattern-how-we-work-desktop.svg) no-repeat right / contain;
}

.find-out-button {
  height: 100%;
  padding: 8px 2rem;
  color: var(--color-neutral-light-grey);
  background: transparent;
  border: 2px solid var(--color-neutral-light-grey);
  font-weight: var(--font-weight-700);
  text-transform: uppercase;
}

.find-out-button:hover {
  cursor: pointer;
  color: var(--color-neutral-very-dark-violet);
  background-color: var(--color-neutral-light-grey);
}

h2 {
  color: var(--color-neutral-light-grey);
  font-size: 56px;
}

@media (max-width: 1180px) {
  #find-out-section {
    margin: 8rem 0;
    padding: 3rem 4rem;
  }
  h2 {
    font-size: 48px;
  }
}

@media (max-width: 768px) {
  #find-out-section {
    margin-top: 5rem;
    padding: 4rem 1rem;
    flex-direction: column;
    text-align: center;
    gap: 3rem;
    background: var(--color-primary-dark-violet)
      url(../assets/images/bg-pattern-how-we-work-mobile.svg) no-repeat right top / 54%;
  }
  h2 {
    font-size: 40px;
  }
  .find-out-button {
    font-size: 14px;
  }
}
</style>
