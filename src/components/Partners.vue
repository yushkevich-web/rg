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
        :class="[
          $style.card,
          {
            [$style.fullWidth]:
              index === cards.length - 1 && cards.length % 2 === 1,
          },
        ]"
        v-for="(card, index) in cards"
        :key="card.name || card.image"
      >
        <div
          :class="[$style.image, card.type ? $style.vertical : '']"
          v-if="card.image"
        >
          <img :src="card.image" :alt="card.name || ''" />
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

    <section :class="$style.friends">
      <h2 :class="$style.friendsTitle">
        {{ $t("partnersSection.friends.title") }}
      </h2>
      <div :class="$style.friendsBody">
        <div :class="$style.friendsCopy">
          <p :class="$style.friendsText">
            {{ $t("partnersSection.friends.firstText") }}
          </p>
          <p :class="$style.friendsText">
            {{ $t("partnersSection.friends.secondText") }}
          </p>
        </div>
        <ul :class="$style.friendsList">
          <li
            v-for="name in friendNames"
            :key="name"
            :class="$style.friendName"
          >
            {{ name }}
          </li>
        </ul>
      </div>
    </section>
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
      friendNamesEn: dataEn.partnersSection.friends.names,
      friendNamesPl: dataPl.partnersSection.friends.names,
      friendNames: [],
    };
  },
  computed: {
    locale() {
      return this.$i18n.locale;
    },
  },
  mounted() {
    this.syncLocaleData();
  },
  watch: {
    locale() {
      this.syncLocaleData();
    },
  },
  methods: {
    syncLocaleData() {
      if (this.$i18n.locale === "en") {
        this.cards = this.dataEn;
        this.friendNames = this.friendNamesEn;
      } else {
        this.cards = this.dataPl;
        this.friendNames = this.friendNamesPl;
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
    margin: 0 0 2rem 0;
    @include custom(750) {
      font-size: 1.8rem;
      line-height: 120%;
      margin-bottom: 1.5rem;
    }
  }
  .cards {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2.5rem 3rem;
    align-items: start;
    @include custom(1050) {
      grid-template-columns: 1fr;
      gap: 1.75rem;
    }
    .card {
      display: flex;
      flex-direction: column;
      min-width: 0;
      &.fullWidth {
        grid-column: 1 / -1;
        @media (min-width: 1051px) {
          display: grid;
          grid-template-columns: auto minmax(0, 1fr);
          align-items: start;
          gap: 1.5rem 2rem;
          .image {
            margin-bottom: 0;
          }
        }
      }
      .name {
        @include F32-600;
        margin: 0 0 0.75rem 0;
        @include custom(560) {
          font-size: 1.5rem;
          line-height: 120%;
        }
      }
      .text {
        @include F28-400;
        line-height: 135%;
        @include custom(560) {
          font-size: 1.5rem;
          line-height: 125%;
        }
      }
      .image {
        display: flex;
        align-items: center;
        height: 5.5rem;
        margin: 0 0 1.25rem 0;
        & img {
          display: block;
          max-height: 100%;
          max-width: 100%;
          width: auto;
          height: auto;
          object-fit: contain;
          object-position: left center;
        }
        @include custom(460) {
          height: 4.5rem;
          margin: 0 auto 1rem auto;
          justify-content: center;
          & img {
            object-position: center;
          }
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

.friends {
  margin-top: 5rem;
  @include custom(1050) {
    margin-top: 4rem;
  }
  @include custom(530) {
    margin-top: 3rem;
  }
}

.friendsTitle {
  @include F64-900;
  margin: 0 0 2.5rem 0;
  text-align: center;
  line-height: 110%;
  @include custom(1080) {
    font-size: 3rem;
  }
  @include custom(750) {
    font-size: 2.2rem;
    margin-bottom: 2rem;
  }
  @include custom(530) {
    font-size: 1.8rem;
    margin-bottom: 1.5rem;
  }
}

.friendsBody {
  display: grid;
  grid-template-columns: minmax(0, 1.05fr) minmax(0, 0.95fr);
  gap: 3rem;
  align-items: start;
  @include custom(1050) {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
}

.friendsCopy {
  min-width: 0;
}

.friendsText {
  @include F28-400;
  margin: 0 0 1.25rem 0;
  font-size: 1.25rem;
  line-height: 150%;
  color: rgba(53, 53, 53, 0.9);
  &:last-child {
    margin-bottom: 0;
  }
  @include custom(1050) {
    font-size: 1.2rem;
  }
  @include custom(530) {
    font-size: 1.1rem;
    line-height: 140%;
  }
}

.friendsList {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 0.75rem;
  margin: 0;
  padding: 0;
  list-style: none;
  @include custom(560) {
    grid-template-columns: 1fr;
  }
}

.friendName {
  @include F28-600;
  margin: 0;
  padding: 0.9rem 1.1rem;
  border-radius: 1rem;
  background-color: rgba(255, 255, 255, 0.92);
  box-shadow: 0 0.35rem 1.25rem rgba(53, 53, 53, 0.05);
  color: $black;
  font-size: 1.1rem;
  line-height: 130%;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  &:hover {
    transform: translateY(-2px);
    box-shadow: 0 0.65rem 1.75rem rgba(53, 53, 53, 0.1);
  }
  @include custom(530) {
    font-size: 1rem;
    padding: 0.85rem 1rem;
  }
}
</style>
