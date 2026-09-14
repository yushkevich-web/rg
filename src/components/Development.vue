<template>
  <div>
    <div :class="$style.wrapper">
      <div :class="$style.container">
        <div :class="$style.title">{{ $t("developmentSection.title") }}</div>
        <div :class="$style.content">
          <article
            v-for="(item, index) in cards"
            :key="item.title"
            :class="[$style.item, index % 2 === 1 ? $style.right : $style.left]"
          >
            <div :class="$style.subtitle">{{ item.title }}</div>
            <div :class="$style.text">{{ item.text }}</div>
          </article>
        </div>
      </div>
    </div>
    <div :class="$style.videoContainer">
      <video
        :class="$style.video"
        controls
        ref="video"
        src="/video/1.mp4"
        type="video/mp4"
      ></video>
    </div>
  </div>
</template>

<script>
import dataEn from "../locales/en.json";
import dataPl from "../locales/pl.json";
export default {
  data() {
    return {
      dataEn: dataEn.developmentSection.cards,
      dataPl: dataPl.developmentSection.cards,
      cards: [],
    };
  },
  computed: {
    locale() {
      return this.$i18n.locale;
    },
  },
  mounted() {
    if (this.$i18n.locale === "en") {
      this.cards = this.dataEn;
    } else {
      this.cards = this.dataPl;
    }
  },
  watch: {
    locale() {
      if (this.$i18n.locale === "en") {
        this.cards = this.dataEn;
      } else {
        this.cards = this.dataPl;
      }
    },
  },
};
</script>

<style lang="scss" module>
.wrapper {
  position: relative;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  background-image: url("../assets/images/bg2.png");
  @include custom(930) {
    background-image: none;
  }
  padding: 4rem 0;
  background-color: $light-brown;
  &::before {
    content: "";
    position: absolute;
    inset: 0;
    background-color: rgba(245, 235, 221, 0.35);
    pointer-events: none;
  }
  .container {
    @include container;
    position: relative;
    z-index: 1;
    .title {
      @include F64-900;
      text-align: center;
      margin: 0 0 3rem 0;
      @include custom(1080) {
        font-size: 3rem;
      }
      @include custom(750) {
        font-size: 2.5rem;
        line-height: 100%;
      }
      @include custom(500) {
        font-size: 2rem;
        margin: 0 0 2rem 0;
        line-height: 100%;
      }
    }
    .content {
      display: flex;
      flex-direction: column;
      gap: 1.5rem;
      @include custom(670) {
        gap: 1.25rem;
      }
    }
    .item {
      width: 100%;
      max-width: 63rem;
      padding: 1.75rem 2rem;
      border-radius: 0.625rem;
      background-color: rgba(255, 255, 255, 0.82);
      @include custom(900) {
        max-width: 54rem;
      }
      @include custom(760) {
        max-width: 100%;
        margin-left: auto;
        margin-right: auto;
      }
      @include custom(670) {
        padding: 1.35rem 1.25rem;
      }
    }
    .left {
      margin-right: auto;
    }
    .right {
      margin-left: auto;
    }
    .subtitle {
      @include F36-600;
      margin: 0 0 0.75rem 0;
      @include custom(1060) {
        font-size: 1.8rem;
      }
      @include custom(500) {
        font-size: 1.5rem;
        line-height: 120%;
      }
    }
    .text {
      @include F28-400;
      line-height: 140%;
      @include custom(1060) {
        font-size: 1.5rem;
      }
      @include custom(530) {
        font-size: 1.1rem;
        line-height: 135%;
      }
    }
  }
}

.videoContainer {
  @include container;
  padding-top: 3rem;
  padding-bottom: 4rem;
  @include custom(670) {
    padding-top: 2rem;
    padding-bottom: 3rem;
  }
}

.video {
  object-fit: cover;
  width: 100%;
  border-radius: 1.25rem;
  max-width: 88.25rem;
  height: 42.375rem;
  display: block;
  margin: 0 auto;
  @include custom(1010) {
    height: 30rem;
  }
  @include custom(670) {
    height: 20rem;
  }
}
</style>
