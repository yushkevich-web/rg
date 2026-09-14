<template>
  <section :class="$style.section">
    <div :class="$style.panel">
      <h2 :class="$style.title">{{ $t("donateCta.title") }}</h2>
      <p :class="$style.text">{{ $t("donateCta.text") }}</p>
      <a
        :class="$style.button"
        href="https://secure.givelively.org/donate/resiliencygardensorg"
        target="_blank"
        rel="noopener noreferrer"
      >
        {{ $t("donateButton") }}
      </a>
    </div>
  </section>
</template>

<style lang="scss" module>
.section {
  @include container;
  margin-bottom: 6.25rem;
  @include tablet {
    margin-bottom: 4rem;
  }
}

.panel {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  max-width: 56rem;
  margin: 0 auto;
  padding: 3rem;
  border-radius: 1.25rem;
  background-color: rgba(255, 255, 255, 0.88);
  box-shadow: 0 0.5rem 2rem rgba(53, 53, 53, 0.06);
  @include custom(760) {
    padding: 2.25rem;
  }
  @include custom(530) {
    padding: 1.75rem 1.5rem;
  }
}

.title {
  @include F64-900;
  margin: 0 0 1.5rem 0;
  line-height: 110%;
  @include custom(1080) {
    font-size: 3rem;
  }
  @include custom(750) {
    font-size: 2.2rem;
  }
  @include custom(530) {
    font-size: 1.8rem;
    margin-bottom: 1.25rem;
  }
}

.text {
  @include F28-400;
  margin: 0 0 2rem 0;
  font-size: 1.35rem;
  line-height: 150%;
  color: rgba(53, 53, 53, 0.9);
  @include custom(1050) {
    font-size: 1.25rem;
  }
  @include custom(530) {
    font-size: 1.1rem;
    line-height: 140%;
    margin-bottom: 1.5rem;
  }
}

.button {
  @include F28-600;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 1rem 2rem;
  border-radius: 0.625rem;
  background-color: $orange;
  color: $white;
  text-decoration: none;
  box-shadow: 0 0.35rem 1.25rem rgba(255, 114, 53, 0.25);
  transition: transform 0.3s ease, box-shadow 0.3s ease,
    background-color 0.3s ease;
  &:hover {
    transform: translateY(-2px);
    box-shadow: 0 0.65rem 1.75rem rgba(255, 114, 53, 0.35);
    background-color: #ff8148;
  }
  @include custom(530) {
    width: 100%;
    font-size: 1.15rem;
    padding: 0.9rem 1.5rem;
  }
}
</style>
