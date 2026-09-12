<template>
  <button
    :class="$style.button"
    type="button"
    @click="changeLanguage($i18n.locale === 'en' ? 'pl' : 'en')"
  >
    {{ $i18n.locale === "en" ? "PL" : "EN" }}
  </button>
</template>

<script>
export default {
  methods: {
    changeLanguage(lang) {
      this.$i18n.locale = lang;
    },
  },
};
</script>

<style lang="scss" module>
.button {
  position: absolute;
  top: 2rem;
  right: 2rem;
  z-index: 101;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  min-width: 4.5rem;
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
  text-transform: uppercase;
  transition: background-color 0.3s ease, color 0.3s ease, box-shadow 0.3s ease,
    transform 0.3s ease;
  &:hover {
    background-color: $orange;
    color: $white;
    box-shadow: 0 0.5rem 1.5rem rgba(255, 114, 53, 0.25);
    transform: translateY(-1px);
  }
  @include custom(530) {
    top: 2rem;
    right: 1rem;
    min-width: 3.5rem;
    padding: 0.75rem 1.25rem;
    font-size: 1rem;
  }
}
</style>
