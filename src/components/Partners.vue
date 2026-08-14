<template>
  <div :class="$style.container">
    <div :class="$style.title">{{ $t("partnersSection.title") }}</div>
    <div :class="$style.subtitle">
      {{ $t("partnersSection.subtext") }}
    </div>
    <div :class="$style.sectionTitle">
      {{ $t("partnersSection.subheading") }}
    </div>
    <div :class="$style.cards">
      <div
        :class="$style.card"
        v-for="card in cards"
        :key="card.name || card.image"
      >
        <div
          :class="[$style.image, card.type ? $style.vertical : '']"
          v-if="card.image"
        >
          <img :src="card.image" alt="" />
        </div>
        <div :class="$style.logoPlaceholder" v-if="card.logoPlaceholder">
          {{ card.logoPlaceholder }}
        </div>
        <a
          :href="card.file"
          target="_blank"
          :class="card.link ? $style.orange : ''"
        >
          <div :class="$style.name" v-if="card.name">{{ card.name }}</div>
          <div :class="$style.text">
            {{ card.text }}
          </div>
          <div :class="$style.link" v-if="card.link">
            {{ card.link }}
            <img src="/icons/arrow-white.svg" alt="" />
          </div>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
import dataEn from "../locales/en.json";
import dataPl from "../locales/pl.json";
export default {
  data() {
    return {
      dataEn: dataEn.partnersSection.cards,
      dataPl: dataPl.partnersSection.cards,
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
.container {
  @include container;
  margin-top: 6.25rem;
  margin-bottom: 6.25rem;
  @include tablet {
    margin-top: 4rem;
    margin-bottom: 4rem;
  }
  .title {
    @include F64-900;
    text-align: center;
    margin: 0 0 2rem 0;
    @include custom(1080) {
      font-size: 3rem;
    }
    @include custom(750) {
      font-size: 2rem;
      margin: 0 0 1rem 0;
      line-height: 100%;
    }
  }
  .subtitle {
    @include F28-400;
    max-width: 74rem;
    text-align: center;
    margin: 0 auto 3rem auto;
    @include custom(1130) {
      font-size: 1.5rem;
      line-height: 120%;
      margin-bottom: 2rem;
    }
  }
  .sectionTitle {
    @include F36-600;
    text-align: center;
    margin: 0 0 3rem 0;
    @include custom(750) {
      font-size: 1.8rem;
      line-height: 120%;
      margin-bottom: 2rem;
    }
  }
  .cards {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4.8rem;
    @include custom(1050) {
      grid-template-columns: 1fr;
      gap: 2rem;
    }
    .card {
      .name {
        @include F32-600;
        margin: 0 0 1rem 0;
        @include custom(560) {
          font-size: 1.5rem;
          line-height: 120%;
        }
      }
      .text {
        @include F28-400;
        @include custom(560) {
          font-size: 1.5rem;
          line-height: 100%;
        }
      }
      .image {
        @include custom(460) {
          max-width: 20rem;
          max-height: 20rem;
          margin: 0 auto 1.5rem auto;
          & img {
            width: 100%;
            height: 100%;
          }
        }
        &.vertical {
          @include custom(460) {
            max-width: 10rem;
            max-height: 10rem;
            margin: 0 auto 1.5rem auto;
            & img {
              width: 100%;
              height: 100%;
            }
          }
        }
      }
      .logoPlaceholder {
        @include F28-600;
        width: 8rem;
        height: 8rem;
        border-radius: 0.625rem;
        background-color: #d9d9d9;
        display: flex;
        align-items: center;
        justify-content: center;
        text-align: center;
        margin: 0 0 1.5rem 0;
        @include custom(460) {
          margin: 0 auto 1.5rem auto;
        }
      }
      .orange {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        height: 100%;
        background-color: $orange;
        border-radius: 1.625rem;
        padding: 1.5rem;
        .text {
          color: $white;
          @include F28-400;
          @include custom(560) {
            font-size: 1.5rem;
            line-height: 100%;
            margin: 0 0 3rem 0;
          }
          @include custom(500) {
            font-size: 1.3rem;
          }
        }
        .link {
          cursor: pointer;
          color: $white;
          display: flex;
          align-items: center;
          @include F28-400;
          @include custom(560) {
            font-size: 1.5rem;
            line-height: 100%;
          }
          @include custom(410) {
            font-size: 1.3rem;
          }
        }
      }
    }
  }
}
</style>
