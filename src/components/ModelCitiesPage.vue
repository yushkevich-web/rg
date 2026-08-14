<template>
  <main :class="$style.page">
    <button :class="$style.back" type="button" @click="goBack">
      <span>←</span>
      {{ $t("modelCitiesPage.back") }}
    </button>
    <LocalSwitcher />

    <section :class="$style.citySection">
      <div :class="$style.imagePlaceholder">placeholder</div>
      <div :class="$style.content">
        <h1 :class="$style.title">{{ $t("modelCitiesPage.rybnik.title") }}</h1>
        <p :class="$style.description">
          {{ $t("modelCitiesPage.rybnik.description") }}
        </p>
      </div>
    </section>

    <section :class="$style.detailSection">
      <h2 :class="$style.sectionTitle">
        {{ $t("modelCitiesPage.rybnik.impactTitle") }}
      </h2>
      <div :class="$style.highlightGrid">
        <div
          v-for="highlight in rybnikHighlights"
          :key="highlight.number"
          :class="$style.highlight"
        >
          <div :class="$style.highlightNumber">{{ highlight.number }}</div>
          <div :class="$style.highlightLabel">
            {{ $t(`modelCitiesPage.rybnik.highlights.${highlight.key}`) }}
          </div>
        </div>
      </div>

      <div :class="$style.awards">
        <article
          v-for="award in rybnikAwards"
          :key="award"
          :class="$style.award"
        >
          <h3 :class="$style.cardTitle">
            {{ $t(`modelCitiesPage.rybnik.awards.${award}.title`) }}
          </h3>
          <p :class="$style.text">
            {{ $t(`modelCitiesPage.rybnik.awards.${award}.description`) }}
          </p>
        </article>
      </div>

      <div :class="$style.sponsors">
        <h3 :class="$style.cardTitle">
          {{ $t("modelCitiesPage.rybnik.sponsorsTitle") }}
        </h3>
        <div :class="$style.sponsorLogos">
          <div
            v-for="sponsor in sponsors"
            :key="sponsor"
            :class="$style.sponsorLogo"
          >
            <img :src="sponsor" alt="" />
          </div>
        </div>
      </div>
    </section>

    <section :class="[$style.citySection, $style.reverse]">
      <div :class="$style.content">
        <h2 :class="$style.title">{{ $t("modelCitiesPage.krakow.title") }}</h2>
        <p :class="$style.description">
          {{ $t("modelCitiesPage.krakow.description") }}
        </p>
      </div>
      <div :class="$style.imagePlaceholder">placeholder</div>
    </section>

    <section :class="$style.detailSection">
      <h2 :class="$style.sectionTitle">
        {{ $t("modelCitiesPage.krakow.highlightsTitle") }}
      </h2>
      <div :class="$style.listHighlights">
        <div
          v-for="highlight in krakowHighlights"
          :key="highlight"
          :class="$style.listHighlight"
        >
          <span>{{
            $t(`modelCitiesPage.krakow.highlights.${highlight}.label`)
          }}</span>
          {{ $t(`modelCitiesPage.krakow.highlights.${highlight}.text`) }}
        </div>
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
      rybnikHighlights: [
        { number: "23", key: "schools" },
        { number: "4,828", key: "students" },
        { number: "197", key: "refugeeStudents" },
        { number: "106", key: "workshops" },
        { number: "2", key: "awards" },
      ],
      rybnikAwards: ["euInnovation", "localGovernment"],
      sponsors: [
        "/images/sponsors/as-logo.png",
        "/images/sponsors/nicknack-logo.jpeg",
        "/images/sponsors/ecol-logo.png",
      ],
      krakowHighlights: [
        "partners",
        "demonstrationSite",
        "tools",
        "training",
        "purpose",
      ],
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

.citySection,
.detailSection {
  @include container;
}

.citySection {
  display: grid;
  grid-template-columns: minmax(18rem, 0.9fr) minmax(0, 1fr);
  align-items: center;
  gap: 4rem;
  margin-bottom: 5rem;
  @include custom(1050) {
    gap: 2rem;
  }
  @include custom(760) {
    grid-template-columns: 1fr;
  }
  &.reverse {
    grid-template-columns: minmax(0, 1fr) minmax(18rem, 0.9fr);
    @include custom(760) {
      grid-template-columns: 1fr;
    }
  }
}

.imagePlaceholder {
  @include F28-600;
  width: 100%;
  aspect-ratio: 1 / 1;
  max-width: 36rem;
  margin: 0 auto;
  border-radius: 0.625rem;
  background-color: #d9d9d9;
  color: $black;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  @include custom(530) {
    font-size: 1.25rem;
  }
}

.content {
  min-width: 0;
}

.title {
  @include F64-900;
  margin: 0 0 2rem 0;
  @include custom(830) {
    font-size: 3rem;
    line-height: 100%;
  }
  @include mobile {
    font-size: 2.8rem;
  }
}

.description,
.text {
  @include F28-400;
  @include custom(1050) {
    font-size: 1.5rem;
    line-height: 120%;
  }
  @include custom(530) {
    font-size: 1.1rem;
  }
}

.detailSection {
  margin-bottom: 6rem;
}

.sectionTitle {
  @include F64-900;
  margin: 0 0 3rem 0;
  text-align: center;
  @include custom(830) {
    font-size: 3rem;
    line-height: 100%;
  }
  @include mobile {
    font-size: 2.8rem;
  }
}

.highlightGrid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 1rem;
  margin-bottom: 2rem;
  @include custom(1050) {
    grid-template-columns: repeat(3, 1fr);
  }
  @include custom(760) {
    grid-template-columns: 1fr;
  }
}

.highlight,
.award,
.sponsors,
.listHighlight {
  border: 0.1875rem solid $black;
  border-radius: 0.625rem;
  background-color: $white;
}

.highlight {
  padding: 1.5rem;
  text-align: center;
}

.highlightNumber {
  @include F64-900;
  color: $orange;
  margin-bottom: 0.5rem;
  @include custom(1050) {
    font-size: 3rem;
    line-height: 100%;
  }
}

.highlightLabel {
  @include F28-600;
  font-size: 1.25rem;
  line-height: 120%;
}

.awards {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 1.5rem;
  margin-bottom: 2rem;
  @include custom(760) {
    grid-template-columns: 1fr;
  }
}

.award,
.sponsors {
  padding: 2rem;
}

.cardTitle {
  @include F32-600;
  margin: 0 0 1rem 0;
  @include custom(530) {
    font-size: 1.5rem;
    line-height: 120%;
  }
}

.sponsorLogos {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  @include custom(640) {
    grid-template-columns: 1fr;
  }
}

.sponsorLogo {
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

.listHighlights {
  display: grid;
  gap: 1rem;
}

.listHighlight {
  @include F28-400;
  padding: 1.5rem;
  line-height: 140%;
  & span {
    @include F28-600;
    color: $green;
  }
  @include custom(530) {
    font-size: 1.1rem;
  }
}
</style>
