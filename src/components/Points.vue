<template>
  <div :class="$style.wrapper">
    <div :class="$style.container">
      <div :class="$style.points">
        <div :class="$style.list">
          <div v-for="item in points" :key="item.title" :class="$style.li">
            <span :class="$style.title" :style="{ color: item.color }">
              {{ item.title }}
            </span>
            <span>{{ item.text }}</span>
          </div>
        </div>
        <div :class="$style.image">
          <img src="/images/points/2.png" alt="" />
        </div>
      </div>
    </div>
    <!-- <div :class="$style.container">
      <div :class="$style.points">
        <div :class="$style.list">
          <div :class="$style.li">
            <div :class="$style.purple">
              People who have access to their own vegetable garden
              <span>consume 40% more</span> fresh vegetables and herbs and,
              consequently, eat less junk food.
            </div>
          </div>
          <div :class="$style.li">
            <div :class="$style.orange">
              Vegetables and herbs lose 30-50% of their useful properties within
              <span>5-10 days.</span> Local vegetable gardens allow you to eat
              vegetables and herbs <span>immediately after harvesting.</span>
            </div>
          </div>
          <div :class="$style.li">
            <div :class="$style.green">
              Working on a garden has a positive effect on personal
              <span> well-being</span>
              and gardening with others enhances
              <span>social connections.</span>
            </div>
          </div>
        </div>
        <div :class="$style.image">
          <img src="/images/points/1.svg" alt="" />
        </div>
      </div>
    </div> -->
  </div>
</template>

<script>
import dataEn from "../locales/en.json";
import dataPl from "../locales/pl.json";
export default {
  data() {
    return {
      dataEn: dataEn.pointsSection,
      dataPl: dataPl.pointsSection,
      points: [],
    };
  },
  computed: {
    locale() {
      return this.$i18n.locale;
    },
  },
  mounted() {
    if (this.$i18n.locale === "en") {
      this.points = this.dataEn;
    } else {
      this.points = this.dataPl;
    }
  },
  watch: {
    locale() {
      if (this.$i18n.locale === "en") {
        this.points = this.dataEn;
      } else {
        this.points = this.dataPl;
      }
    },
  },
};
</script>

<style lang="scss" module>
.wrapper {
  margin: 14rem 0 0 0;
  @include custom(1325) {
    margin: 5rem 0 0 0;
  }
  .container {
    @include container;
    .points {
      display: grid;
      grid-template-columns: 1fr 1fr;
      align-items: end;
      gap: 1rem;
      margin: 0 0 6.25rem 0;
      @include tablet {
        grid-template-columns: 1fr;
        margin: 0 0 4rem 0;
      }
      .list {
        @include tablet {
          order: 2;
        }
        .li {
          margin: 0 0 1.25rem 0;
          @include F32-500;
          @include custom(1100) {
            font-size: 1.5rem;
            line-height: 120%;
          }
          @include custom(870) {
            font-size: 1.35rem;
          }
          @include custom(530) {
            font-size: 1.1rem;
          }
          &:last-child {
            margin: 0;
          }
        }
        .purple {
          & span {
            color: $purple;
          }
        }
        .orange {
          & span {
            color: $orange;
          }
        }
        .green {
          & span {
            color: $green;
          }
        }
      }
      .image {
        max-width: 50rem;
        max-height: 50rem;
        & img {
          width: 100%;
          height: 100%;
        }
        @include tablet {
          order: 1;
          margin: 0 0 2rem 0;
        }
      }
    }
  }
}
</style>
