<template>
  <div class="page page--how-it-works">
    <Navbar />

    <Hero>
      <div
        slot="title"
        class="hero__title"
        style="font-family: gilroy-bold; font-size: 2.4rem;"
      >
        Here’s how we save you.
      </div>
      <div
        slot="description"
        class="hero__description"
        style="font-family: gilroy-medium; font-size: .85rem;"
      >
        We mash together one-way flights from different carriers to get the
        cheapest options available. 80% of the time, this process alone gets you
        the best deal in the internet. We’re so good at it that we even call
        ourselves FlyLine! (FlyVirtualInterLine just doesn’t have the same ring
        to it)
      </div>
    </Hero>

    <Container :dark="false" class="container--timeline">
      <section class="timeline-hiw">
        <h3 class="timeline__title" style="font-family: gilroy-bold;">
          What do I need to know?
        </h3>

        <div
          :class="{
            timeline__item: true,
            'timeline__item--reverse': i % 2 === 1
          }"
          v-for="(item, i) in timeline"
          :key="i"
        >
          <!-- <span class="timeline__item__bullet">
            <span class="icon" v-text="i + 1 < 10 ? `0${i + 1}` : i + 1"></span>
          </span> -->

          <div class="timeline__item__content">
            <div class="timeline__item__img">
              <img :src="item.img" alt="Timeline image" />
            </div>

            <div class="timeline__item__text">
              <h5 v-text="item.title"></h5>
              <p v-text="item.body"></p>
            </div>
          </div>

          <div class="timeline__item__separate">
            <div class="timeline__item__line" v-show="!item.next && item.line">
              <img :src="item.line" alt="Timeline Line" />

              <div
                class="timeline__item__number"
                :class="['timeline__item__number--' + (i + 1)]"
              >
                <img :src="item.number" alt="Timeline Number" />
              </div>
            </div>

            <div class="timeline__item__line" v-show="item.next">
              <img :src="item.line" alt="Timeline Line" />

              <div
                class="timeline__item__number"
                :class="['timeline__item__number--' + (i + 1)]"
              >
                <img :src="item.number" alt="Timeline Number" />
              </div>

              <div
                class="timeline__item__number"
                :class="['timeline__item__number--' + (i + 2)]"
              >
                <img :src="item.next" alt="Timeline Number" />
              </div>
            </div>
          </div>
        </div>
      </section>
    </Container>

    <SubFooter
      titleOne="Learn More"
      titleTwo="Request Access"
      linkOne="How it works"
      linkTwo="Pricing"
    ></SubFooter>

    <Footer />
  </div>
</template>

<script>
import Hero from "@/components/molecules/Hero";
import Navbar from "@/components/organisms/Navbar";
import Footer from "@/components/organisms/Footer";
import Container from "@/components/molecules/Container";
import SubFooter from "@/components/molecules/HowItWorks/SubFooter";

export default {
  name: "HowItWorks",
  components: {
    Hero,
    Navbar,
    Footer,
    Container,
    SubFooter
  },
  computed: {
    timeline() {
      return [
        {
          title: "The best fares from everywhere",
          img: "/images/how-it-works/international-flights.svg",
          line: "/images/how-it-works/line-one.svg",
          number: "/images/how-it-works/one.svg",
          body:
            "Search fares from more than 250 airlines from a single place. Save all your traveler information so you can book with a click."
        },
        {
          title: "Get deals delivered",
          img: "/images/how-it-works/legacy-carriers.svg",
          line: "/images/how-it-works/line-two.svg",
          number: "/images/how-it-works/two.svg",
          body:
            "Set a few preferences and our army of internet robots will do the searching for you. We’ll alert you the second we find a great deal, which can be up to 60% off a standard fare."
        },
        {
          title: "Automatically book the best",
          img: "/images/how-it-works/major-cities.svg",
          line: "/images/how-it-works/line-three.svg",
          number: "/images/how-it-works/three.svg",
          body:
            "The best fares go fast. FlyLine can auto-book fares that meet your preferences so you won’t miss out. You’ll have 24 hours to confirm — if you don’t confirm you don’t pay."
        },
        {
          title: "Manage trips from your dedicated flightdeck (that’s us)",
          img: "/images/how-it-works/compare-the-fare.svg",
          line: "/images/how-it-works/line-four.svg",
          number: "/images/how-it-works/four.svg",
          next: "/images/how-it-works/five.svg",
          body:
            "Use FlyLine to manage all the details of your flights, just like you would from the airlines’ sites. Select seats, make updates and cancellations, check upgrades, and more."
        },
        {
          title: "A subscription that pays for itself",
          img: "/images/how-it-works/deal-alerts.svg",
          body:
            "Everything’s included in your subscription fee, which most members earn back with just two bookings. No fare markups, no booking fees, no surprises."
        }
      ];
    }
  }
};
</script>

<style lang="scss">
.page--how-it-works {
  font-family: "Gilroy-Regular", sans-serif;
  display: flex;
  flex-flow: column wrap;
  align-items: center;

  > .hero {
    margin-top: 3.5rem;
    padding: 2.5rem 3.5rem;
    width: 960px;
    box-shadow: 20px 40px 70px 0 rgba(0, 0, 0, 0.16);
  }

  > .container {
    &--timeline {
      margin-top: 4rem;
    }

    &--padded {
      padding: 2.5rem;
    }
  }

  .timeline-hiw {
    display: flex;
    align-items: center;
    flex-flow: column nowrap;
  }

  .timeline-hiw {
    .timeline {
      &__title {
        font-size: 1.8rem;
        font-family: "Gilroy-Medium";
        letter-spacing: 1.5px;
        color: #0e3178;
        margin-bottom: 3.5rem;
      }

      &__item {
        display: flex;
        align-items: flex-start;
        justify-content: center;
        flex-flow: row wrap;
        padding: 0.5rem 0;

        &--reverse {
          .timeline__item {
            &__content {
              flex-flow: row-reverse wrap;
            }
            &__img {
              text-align: right;
            }
          }
        }

        &__content {
          display: flex;
          align-items: center;
          flex-flow: row wrap;
        }

        &__img {
          width: 35%;
          text-align: left;
        }
        &__text {
          width: 50%;
          margin-left: 3%;
        }

        &__text {
          background-color: transparent;
          padding: 0 1.5rem;
          border-radius: 1rem;
          border-top-left-radius: 0;

          h5 {
            font-family: gilroy-bold;
            font-size: 1.6rem;
            font-weight: 600;
            margin-bottom: 1.5rem;
          }

          p {
            color: #7b7b7b;
            font-size: 1rem;
            margin-bottom: 0;
            font-family: "Gilroy-Medium";
          }
        }

        &__line {
          padding-top: 1rem;
          width: 88%;
          margin-left: 12%;
          position: relative;
        }

        &__number {
          position: absolute;
          left: -16px;
          top: 50%;
          transform: translateY(-50%);

          &--2 {
            top: 65%;
            right: -16px;
            left: unset;
          }
          &--3 {
            top: 38%;
          }
          &--4 {
            top: 53%;
          }
          &--5 {
            right: -16px;
            left: unset;
          }
        }
      }

      &__item:last-child {
        .timeline__item__bullet::after {
          height: 0;
        }
      }
    }
  }
}
</style>
