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
          <div :class="[$style.logo, { [$style.logoDark]: partner.darkLogo }]">
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
          darkLogo: true,
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
  background-image: linear-gradient(
    180deg,
    rgba(255, 255, 255, 0.35) 0%,
    rgba(245, 235, 221, 0) 40%,
    rgba(160, 196, 198, 0.12) 100%
  );
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
  padding: 0.875rem 1.5rem;
  border: none;
  border-radius: 999px;
  background-color: rgba(255, 255, 255, 0.92);
  box-shadow: 0 0.25rem 1.25rem rgba(53, 53, 53, 0.08);
  color: $black;
  cursor: pointer;
  @include F28-600;
  font-size: 1.25rem;
  line-height: 120%;
  transition: background-color 0.3s ease, color 0.3s ease, box-shadow 0.3s ease,
    transform 0.3s ease;
  &:hover {
    background-color: $orange;
    color: $white;
    box-shadow: 0 0.5rem 1.5rem rgba(255, 114, 53, 0.25);
    transform: translateY(-1px);
  }
  @include custom(530) {
    left: 1rem;
    padding: 0.75rem 1.25rem;
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
  margin: 0 auto 3.5rem auto;
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
  font-size: 1.25rem;
  line-height: 145%;
  max-width: 100%;
  margin: 0 0 3rem 0;
  padding: 1.5rem 2rem;
  border-radius: 1.25rem;
  background-color: rgba(255, 255, 255, 0.72);
  box-shadow: 0 0.25rem 1.5rem rgba(53, 53, 53, 0.05);
  text-align: center;
  @include custom(1050) {
    font-size: 1.2rem;
  }
  @include custom(530) {
    font-size: 1.1rem;
    line-height: 140%;
    padding: 1.25rem 1.25rem;
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
  border-radius: 1.25rem;
  background-color: rgba(255, 255, 255, 0.88);
  box-shadow: 0 0.5rem 2rem rgba(53, 53, 53, 0.06);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  &:hover {
    transform: translateY(-3px);
    box-shadow: 0 0.75rem 2.5rem rgba(53, 53, 53, 0.1);
  }
}

.partnerCard {
  display: grid;
  grid-template-columns: 12rem minmax(0, 1fr);
  gap: 1.5rem;
  align-items: center;
  padding: 1.75rem;
  @include custom(1050) {
    grid-template-columns: 9rem minmax(0, 1fr);
  }
  @include custom(530) {
    grid-template-columns: 1fr;
    padding: 1.5rem;
  }
}

.logo {
  min-height: 10rem;
  border-radius: 1rem;
  background-color: transparent;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1.25rem;
  & img {
    max-width: 100%;
    max-height: 8rem;
    display: block;
    object-fit: contain;
  }
}

.logoDark {
  background-color: #a08970;
  padding: 1.5rem;
  & img {
    max-height: 7rem;
  }
}

.educatorCard {
  padding: 2rem;
  @include custom(530) {
    padding: 1.5rem;
  }
}

.year {
  @include F28-600;
  display: inline-block;
  margin-bottom: 1rem;
  padding: 0.5rem 1.125rem;
  border-radius: 999px;
  background-color: $orange;
  color: $white;
  font-size: 1.15rem;
  line-height: 120%;
  box-shadow: 0 0.25rem 0.75rem rgba(255, 114, 53, 0.25);
}

.cardTitle {
  @include F32-600;
  margin: 0 0 1rem 0;
  line-height: 130%;
  @include custom(530) {
    font-size: 1.5rem;
  }
}

.school {
  @include F28-600;
  margin-bottom: 1rem;
  font-size: 1.25rem;
  line-height: 140%;
  color: $green;
  @include custom(530) {
    font-size: 1.1rem;
  }
}

.text {
  @include F28-400;
  font-size: 1.25rem;
  line-height: 150%;
  color: rgba(53, 53, 53, 0.9);
  @include custom(530) {
    font-size: 1.1rem;
    line-height: 130%;
  }
}
</style>
