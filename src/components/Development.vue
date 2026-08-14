<template>
  <div>
    <div :class="$style.wrapper">
      <div :class="$style.container">
        <div :class="$style.title">{{ $t("developmentSection.title") }}</div>
        <div :class="$style.content">
          <div
            v-for="(item, index) in cards"
            :key="item.title"
            :class="[$style.row, { [$style.reverse]: index % 2 === 1 }]"
          >
            <div :class="$style.copy">
              <div :class="$style.subtitle">{{ item.title }}</div>
              <div :class="$style.text">{{ item.text }}</div>
            </div>
            <div :class="$style.placeholder">placeholder</div>
          </div>
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
  // margin-top: 5rem;
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
      margin: 0 0 2rem 0;
      @include custom(1080) {
        font-size: 3rem;
      }
      @include custom(750) {
        font-size: 2.5rem;
        line-height: 100%;
      }
      @include custom(500) {
        font-size: 2rem;
        margin: 0 0 1rem 0;
        line-height: 100%;
      }
    }
    .content {
      margin: 0 0 3rem 0;
      @include custom(1010) {
        margin: 0 0 2.5rem 0;
      }
      @include custom(670) {
        margin: 0 0 2rem 0;
      }
      .row {
        display: grid;
        grid-template-columns: minmax(0, 1fr) minmax(14rem, 0.45fr);
        align-items: center;
        gap: 2.5rem;
        margin: 0 0 2.5rem 0;
        &:last-child {
          margin-bottom: 0;
        }
        @include custom(970) {
          gap: 1.5rem;
        }
        @include custom(660) {
          grid-template-columns: 1fr;
          gap: 1.5rem;
          margin: 0 0 3rem 0;
        }
        &.reverse {
          grid-template-columns: minmax(14rem, 0.45fr) minmax(0, 1fr);
          .placeholder {
            order: 1;
          }
          .copy {
            order: 2;
          }
          @include custom(660) {
            grid-template-columns: 1fr;
          }
        }
      }
      .copy {
        padding: 1.5rem;
        border-radius: 0.625rem;
        background-color: rgba(255, 255, 255, 0.82);
        @include custom(660) {
          order: 2;
          padding: 1.25rem;
        }
      }
      .placeholder {
        @include F28-600;
        width: 100%;
        aspect-ratio: 1 / 1;
        max-width: 18rem;
        margin: 0 auto;
        border-radius: 0.625rem;
        background-color: #d9d9d9;
        color: $black;
        display: flex;
        align-items: center;
        justify-content: center;
        text-align: center;
        @include custom(660) {
          order: 1;
        }
        @include custom(530) {
          font-size: 1.25rem;
        }
      }
      .subtitle {
        @include F36-600;
        margin: 0 0 1rem 0;
        @include custom(1060) {
          font-size: 1.8rem;
        }
      }
      .text {
        @include F28-400;
        @include custom(1060) {
          font-size: 1.5rem;
        }
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
