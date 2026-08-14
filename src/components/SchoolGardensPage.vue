<template>
  <main :class="$style.page">
    <button :class="$style.back" type="button" @click="goBack">
      <span>←</span>
      {{ $t("schoolGardensPage.back") }}
    </button>
    <LocalSwitcher />

    <section :class="$style.hero">
      <div :class="$style.content">
        <h1 :class="$style.title">{{ $t("schoolGardensPage.title") }}</h1>
        <div :class="$style.stats">
          <div :class="$style.stat">
            <div :class="$style.number">36</div>
            <div :class="$style.label">
              {{ $t("schoolGardensPage.stats.schoolGardens") }}
            </div>
          </div>
          <div :class="$style.stat">
            <div :class="$style.number">6,350+</div>
            <div :class="$style.label">
              {{ $t("schoolGardensPage.stats.students") }}
            </div>
          </div>
          <div :class="$style.stat">
            <div :class="$style.number">401+</div>
            <div :class="$style.label">
              {{ $t("schoolGardensPage.stats.refugeeStudents") }}
            </div>
          </div>
        </div>
        <p :class="$style.description">
          {{ $t("schoolGardensPage.description") }}
        </p>
      </div>
    </section>

    <section :class="$style.locator">
      {{ $t("schoolGardensPage.locatorPlaceholder") }}
    </section>
  </main>
</template>

<script>
import LocalSwitcher from "./LocalSwitcher.vue";

export default {
  components: {
    LocalSwitcher,
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

.hero,
.locator {
  @include container;
}

.hero {
  margin-bottom: 5rem;
}

.content {
  max-width: 74rem;
  margin: 0 auto;
  text-align: center;
}

.title {
  @include F64-900;
  margin: 0 0 3rem 0;
  @include custom(830) {
    font-size: 3rem;
    line-height: 100%;
  }
  @include mobile {
    font-size: 2.8rem;
  }
}

.stats {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
  margin-bottom: 3rem;
  @include custom(760) {
    grid-template-columns: 1fr;
  }
}

.stat {
  padding: 2rem 1.5rem;
  border-radius: 0.625rem;
  background-color: $white;
  border: 0.1875rem solid $black;
}

.number {
  @include F64-900;
  color: $orange;
  margin-bottom: 0.75rem;
  @include custom(1050) {
    font-size: 3rem;
    line-height: 100%;
  }
}

.label {
  @include F28-600;
  line-height: 120%;
  @include custom(1050) {
    font-size: 1.4rem;
  }
  @include custom(530) {
    font-size: 1.1rem;
  }
}

.description {
  @include F28-400;
  max-width: 62rem;
  margin: 0 auto;
  @include custom(1050) {
    font-size: 1.5rem;
    line-height: 120%;
  }
  @include custom(530) {
    font-size: 1.1rem;
  }
}

.locator {
  min-height: 24rem;
  border: 0.1875rem dashed $black;
  border-radius: 0.625rem;
  background-color: #d9d9d9;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  @include F36-600;
  color: $black;
  @include custom(530) {
    min-height: 18rem;
    font-size: 1.5rem;
  }
}
</style>
