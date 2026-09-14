<template>
  <main :class="$style.page">
    <button :class="$style.back" type="button" @click="goBack">
      <span>←</span>
      {{ $t("modelCitiesPage.back") }}
    </button>
    <LocalSwitcher />

    <section :class="$style.citySection">
      <div :class="$style.image">
        <img
          src="/images/work/img-rybnik.jpg"
          :alt="$t('modelCitiesPage.rybnik.title')"
        />
      </div>
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
      <div :class="$style.image">
        <img
          src="/images/work/img-cracow.jpg"
          :alt="$t('modelCitiesPage.krakow.title')"
        />
      </div>
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

.citySection,
.detailSection {
  @include container;
}

.citySection {
  display: grid;
  grid-template-columns: minmax(16rem, 0.85fr) minmax(0, 1fr);
  align-items: center;
  gap: 2.5rem;
  margin-bottom: 3.5rem;
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

.image {
  width: 100%;
  max-width: 28rem;
  margin: 0 auto;
  & img {
    width: 100%;
    aspect-ratio: 1 / 1;
    object-fit: cover;
    display: block;
    border-radius: 1.25rem;
    box-shadow: 0 0.5rem 2rem rgba(53, 53, 53, 0.06);
  }
}

.content {
  min-width: 0;
  padding: 1.5rem 1.75rem;
  border-radius: 1.25rem;
  background-color: rgba(255, 255, 255, 0.72);
  box-shadow: 0 0.25rem 1.5rem rgba(53, 53, 53, 0.05);
  @include custom(760) {
    padding: 1.25rem;
  }
}

.title {
  @include F64-900;
  font-size: 2.75rem;
  line-height: 110%;
  margin: 0 0 1.25rem 0;
  @include custom(830) {
    font-size: 2.5rem;
  }
  @include mobile {
    font-size: 2.25rem;
  }
}

.description,
.text {
  @include F28-400;
  font-size: 1.15rem;
  line-height: 145%;
  color: rgba(53, 53, 53, 0.9);
  @include custom(530) {
    font-size: 1rem;
    line-height: 135%;
  }
}

.detailSection {
  margin-bottom: 4rem;
  &:last-child {
    margin-bottom: 0;
  }
}

.sectionTitle {
  @include F64-900;
  font-size: 2.75rem;
  line-height: 110%;
  margin: 0 0 2rem 0;
  text-align: center;
  @include custom(830) {
    font-size: 2.5rem;
  }
  @include mobile {
    font-size: 2.25rem;
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
.sponsors {
  border-radius: 1.25rem;
  background-color: rgba(255, 255, 255, 0.88);
  box-shadow: 0 0.5rem 2rem rgba(53, 53, 53, 0.06);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  &:hover {
    transform: translateY(-3px);
    box-shadow: 0 0.75rem 2.5rem rgba(53, 53, 53, 0.1);
  }
}

.highlight {
  position: relative;
  padding: 1.25rem 1rem;
  text-align: center;
  overflow: hidden;
  &::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 0.375rem;
    border-radius: 1.25rem 1.25rem 0 0;
  }
  &:nth-child(1)::before {
    background: linear-gradient(90deg, $orange, lighten($orange, 12%));
  }
  &:nth-child(2)::before {
    background: linear-gradient(90deg, $yellow, lighten($yellow, 10%));
  }
  &:nth-child(3)::before {
    background: linear-gradient(90deg, $light-blue, lighten($light-blue, 10%));
  }
  &:nth-child(4)::before {
    background: linear-gradient(90deg, $green, lighten($green, 10%));
  }
  &:nth-child(5)::before {
    background: linear-gradient(90deg, $purple, lighten($purple, 10%));
  }
}

.highlightNumber {
  font-family: "Manrope", sans-serif;
  font-weight: 700;
  font-size: 2.5rem;
  line-height: 100%;
  margin-bottom: 0.35rem;
  @include custom(1050) {
    font-size: 2.25rem;
  }
  .highlight:nth-child(1) & {
    color: $orange;
  }
  .highlight:nth-child(2) & {
    color: darken($yellow, 18%);
  }
  .highlight:nth-child(3) & {
    color: $light-blue;
  }
  .highlight:nth-child(4) & {
    color: $green;
  }
  .highlight:nth-child(5) & {
    color: $purple;
  }
}

.highlightLabel {
  @include F28-600;
  font-size: 0.95rem;
  line-height: 125%;
  color: rgba(53, 53, 53, 0.85);
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
  padding: 1.5rem 1.75rem;
  @include custom(530) {
    padding: 1.25rem;
  }
}

.cardTitle {
  @include F32-600;
  font-size: 1.35rem;
  line-height: 125%;
  margin: 0 0 0.75rem 0;
  @include custom(530) {
    font-size: 1.2rem;
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
  min-height: 7rem;
  border-radius: 1rem;
  background-color: transparent;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0.75rem;
  & img {
    max-width: 100%;
    max-height: 5.5rem;
    display: block;
    object-fit: contain;
  }
}

.listHighlights {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.25rem 2.5rem;
  max-width: 44rem;
  margin: 0 auto;
  padding: 1.75rem 2rem;
  border-radius: 1.25rem;
  background-color: rgba(255, 255, 255, 0.88);
  box-shadow: 0 0.5rem 2rem rgba(53, 53, 53, 0.06);
  @include custom(530) {
    grid-template-columns: 1fr;
    gap: 1rem;
    padding: 1.25rem;
  }
}

.listHighlight {
  @include F28-400;
  font-size: 1rem;
  line-height: 140%;
  & span {
    @include F28-600;
    display: block;
    margin-bottom: 0.25rem;
    font-size: 0.9rem;
    line-height: 125%;
    color: $green;
  }
  &:last-child {
    grid-column: 1 / -1;
  }
  @include custom(530) {
    font-size: 0.95rem;
    &:last-child {
      grid-column: auto;
    }
  }
}
</style>
