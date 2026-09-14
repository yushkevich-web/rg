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

.hero {
  @include container;
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
  @include custom(760) {
    grid-template-columns: 1fr;
    max-width: 28rem;
    margin-left: auto;
    margin-right: auto;
  }
}

.stat {
  position: relative;
  padding: 2.25rem 1.5rem;
  border-radius: 1.25rem;
  background-color: rgba(255, 255, 255, 0.88);
  box-shadow: 0 0.5rem 2rem rgba(53, 53, 53, 0.06);
  overflow: hidden;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  &:hover {
    transform: translateY(-3px);
    box-shadow: 0 0.75rem 2.5rem rgba(53, 53, 53, 0.1);
  }
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
}

.number {
  font-family: "Manrope", sans-serif;
  font-weight: 700;
  font-size: 4rem;
  line-height: 4.5rem;
  margin-bottom: 0.75rem;
  @include custom(1050) {
    font-size: 3rem;
    line-height: 100%;
  }
  .stat:nth-child(1) & {
    color: $orange;
  }
  .stat:nth-child(2) & {
    color: darken($yellow, 18%);
  }
  .stat:nth-child(3) & {
    color: $light-blue;
  }
}

.label {
  @include F28-600;
  line-height: 130%;
  color: rgba(53, 53, 53, 0.85);
  @include custom(1050) {
    font-size: 1.4rem;
  }
  @include custom(530) {
    font-size: 1.1rem;
  }
}
</style>
