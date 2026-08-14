<template>
  <main :class="$style.page">
    <button :class="$style.back" type="button" @click="goBack">
      <span>←</span>
      {{ $t("educationalPartnersPage.back") }}
    </button>
    <LocalSwitcher />

    <section :class="$style.section">
      <h1 :class="$style.title">{{ $t("educationalPartnersPage.title") }}</h1>
      <div :class="$style.partnerGrid">
        <article
          v-for="partner in partners"
          :key="partner.key"
          :class="$style.partnerCard"
        >
          <div :class="$style.logo">
            <img
              :src="partner.logo"
              :alt="$t(`educationalPartnersPage.partners.${partner.key}.name`)"
            />
          </div>
          <div>
            <h2 :class="$style.cardTitle">
              {{ $t(`educationalPartnersPage.partners.${partner.key}.name`) }}
            </h2>
            <p :class="$style.text">
              {{
                $t(
                  `educationalPartnersPage.partners.${partner.key}.description`
                )
              }}
            </p>
          </div>
        </article>
      </div>
    </section>

    <section :class="$style.section">
      <h2 :class="$style.sectionTitle">
        {{ $t("educationalPartnersPage.educators.title") }}
      </h2>
      <p :class="$style.intro">
        {{ $t("educationalPartnersPage.educators.intro") }}
      </p>
      <div :class="$style.educatorGrid">
        <article
          v-for="educator in educators"
          :key="educator"
          :class="$style.educatorCard"
        >
          <div :class="$style.year">
            {{ $t(`educationalPartnersPage.educators.items.${educator}.year`) }}
          </div>
          <h3 :class="$style.cardTitle">
            {{ $t(`educationalPartnersPage.educators.items.${educator}.name`) }}
          </h3>
          <div :class="$style.school">
            {{
              $t(`educationalPartnersPage.educators.items.${educator}.school`)
            }}
          </div>
          <p :class="$style.text">
            {{
              $t(
                `educationalPartnersPage.educators.items.${educator}.description`
              )
            }}
          </p>
        </article>
      </div>
    </section>
  </main>
</template>

<script>
import LocalSwitcher from "./LocalSwitcher.vue";

export default {
  components: {
    LocalSwitcher,
  },
  data() {
    return {
      partners: [
        {
          key: "tripsBeyondClassroom",
          logo: "/images/partner-logos/beyondClassrooms.png",
        },
        {
          key: "fundacjaRozwoju",
          logo: "/images/partner-logos/FundacjaRozwoju.jpeg",
        },
        {
          key: "ogrodZKlasa",
          logo: "/images/partner-logos/ogdrodZKlasa.png",
        },
        {
          key: "ogrodPodGwiazdami",
          logo: "/images/partner-logos/podGwiazdami.png",
        },
      ],
      educators: ["bozena", "anna", "tomasz", "dagmara"],
    };
  },
  mounted() {
    this.scrollToTop();
  },
  methods: {
    goBack() {
      window.location.hash = "#solution";
    },
    scrollToTop() {
      const reset = () => {
        window.scrollTo(0, 0);
        document.documentElement.scrollTop = 0;
        document.body.scrollTop = 0;
      };

      reset();
      requestAnimationFrame(reset);
      setTimeout(reset, 50);
    },
  },
};
</script>

<style lang="scss" module>
.page {
  min-height: 100vh;
  position: relative;
  padding: 8rem 1rem 6rem 1rem;
  background-color: $light-brown;
  color: $black;
  @include custom(530) {
    padding-top: 7rem;
    padding-bottom: 4rem;
  }
}

.back {
  position: absolute;
  top: 2rem;
  left: 2rem;
  z-index: 101;
  display: inline-flex;
  align-items: center;
  gap: 0.75rem;
  padding: 1rem 1.5rem;
  border: 0.1875rem solid $black;
  border-radius: 0.625rem;
  background-color: $white;
  color: $black;
  cursor: pointer;
  @include F28-600;
  font-size: 1.35rem;
  line-height: 120%;
  transition: all 0.3s ease-in-out;
  &:hover {
    background-color: $black;
    color: $white;
  }
  @include custom(530) {
    left: 1rem;
    padding: 0.75rem 1rem;
    font-size: 1rem;
  }
}

.section {
  @include container;
  margin-bottom: 5rem;
  &:last-child {
    margin-bottom: 0;
  }
}

.title {
  @include F64-900;
  max-width: 64rem;
  margin: 0 auto 4rem auto;
  text-align: center;
  @include custom(830) {
    font-size: 3rem;
    line-height: 100%;
  }
  @include mobile {
    font-size: 2.8rem;
  }
}

.sectionTitle {
  @include F64-900;
  margin: 0 0 2rem 0;
  text-align: center;
  @include custom(830) {
    font-size: 3rem;
    line-height: 100%;
  }
  @include mobile {
    font-size: 2.8rem;
  }
}

.intro {
  @include F28-400;
  max-width: 72rem;
  margin: 0 auto 3rem auto;
  text-align: center;
  @include custom(1050) {
    font-size: 1.5rem;
    line-height: 120%;
  }
  @include custom(530) {
    font-size: 1.1rem;
  }
}

.partnerGrid,
.educatorGrid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 1.5rem;
  @include custom(800) {
    grid-template-columns: 1fr;
  }
}

.partnerCard,
.educatorCard {
  border: 0.1875rem solid $black;
  border-radius: 0.625rem;
  background-color: $white;
}

.partnerCard {
  display: grid;
  grid-template-columns: 12rem minmax(0, 1fr);
  gap: 1.5rem;
  align-items: center;
  padding: 1.5rem;
  @include custom(1050) {
    grid-template-columns: 9rem minmax(0, 1fr);
  }
  @include custom(530) {
    grid-template-columns: 1fr;
  }
}

.logo {
  min-height: 10rem;
  border-radius: 0.625rem;
  background-color: $light-brown;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1rem;
  & img {
    max-width: 100%;
    max-height: 8rem;
    display: block;
    object-fit: contain;
  }
}

.educatorCard {
  padding: 2rem;
}

.year {
  @include F28-600;
  display: inline-block;
  margin-bottom: 1rem;
  padding: 0.5rem 1rem;
  border-radius: 999px;
  background-color: $orange;
  color: $white;
  font-size: 1.25rem;
  line-height: 120%;
}

.cardTitle {
  @include F32-600;
  margin: 0 0 1rem 0;
  @include custom(530) {
    font-size: 1.5rem;
    line-height: 120%;
  }
}

.school {
  @include F28-600;
  margin-bottom: 1rem;
  font-size: 1.35rem;
  line-height: 140%;
  color: $green;
  @include custom(530) {
    font-size: 1.1rem;
  }
}

.text {
  @include F28-400;
  font-size: 1.35rem;
  line-height: 150%;
  @include custom(530) {
    font-size: 1.1rem;
    line-height: 120%;
  }
}
</style>
