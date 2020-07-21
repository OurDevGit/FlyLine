<template>
  <div
    style="margin-top: 150px; margin-bottom: 100px;"
    class="hero hero--footer"
  >
    <div class="hero__header">
      <h4 class="hero__subtitle">Don't miss out on the savings</h4>
      <h3 class="hero__title">Get started with FlyLine Today</h3>
    </div>
    <div class="hero__links">
      <Button type="primary" @click="goTo('How it works')"
        >Download the App</Button
      >
      <Button type="primary" @click="goTo('Pricing')">Learn More</Button>
    </div>
  </div>
</template>

<script>
import Button from "@/components/atoms/Button.vue";

export default {
  name: "SubFooter",
  components: {
    Button
  },
  methods: {
    goTo(page) {
      this.$router.push({ name: page });
    }
  }
};
</script>

<style scoped lang="scss">
.hero {
  &--footer {
    display: flex;
    flex-flow: row wrap;
    justify-content: space-between;
    align-items: center;
    flex-grow: 1;
    padding: 4rem;
    color: #fff;
    background-color: #0e3178;
    box-shadow: 5px 5px 50px 0 rgba(14, 49, 120, 0.3);
    border-radius: 1rem;

    .hero {
      &__title {
        padding-bottom: 0;
        margin: 0;
        font-family: "Gilroy-Bold", sans-serif;
        font-size: 1.5rem;
        font-weight: 400;
      }

      &__subtitle {
        padding-bottom: 0.5rem;
        margin: 0;
        font-family: "Gilroy-Light", sans-serif;
        font-size: 0.75rem;
        letter-spacing: 0.15rem;
        text-transform: uppercase;
      }

      &__links {
        display: flex;
        justify-content: center;
        align-items: center;

        > .btn {
          width: auto;
          height: auto;
          padding: 0.8rem 1.6rem;
          font-size: 0.7rem;
          box-shadow: none;

          &--outline {
            color: #fff;
            border-color: #fff;
            opacity: 0.5;
          }

          &:first-child {
            margin-right: 1rem;
          }
        }
      }
    }
  }
}
</style>
