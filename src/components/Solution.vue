<template>
  <div :class="$style.container">
    <div :class="$style.title">{{ $t("solutionSection.title") }}</div>
    <div :class="$style.description">
      {{ $t("solutionSection.description") }}
    </div>
    <div :class="$style.schoolGardensBlock">
      <div :class="$style.placeholder">picture/slider</div>
      <div :class="$style.featureText">
        <div :class="$style.subtitle">
          {{ $t("solutionSection.schoolGardens.title") }}
        </div>
        <div :class="$style.text">
          <p>{{ $t("solutionSection.schoolGardens.firstText") }}</p>
          <p>{{ $t("solutionSection.schoolGardens.secondText") }}</p>
        </div>
        <button :class="$style.button" @click="scrollTo('#winners')">
          {{ $t("solutionSection.schoolGardens.learnMore") }}
        </button>
      </div>
    </div>
    <div :class="[$style.schoolGardensBlock, $style.reverse]">
      <div :class="$style.featureText">
        <div :class="$style.subtitle">
          {{ $t("solutionSection.educationalPartners.title") }}
        </div>
        <div :class="$style.text">
          <p>{{ $t("solutionSection.educationalPartners.firstText") }}</p>
          <p>{{ $t("solutionSection.educationalPartners.secondText") }}</p>
        </div>
        <button :class="$style.button" @click="scrollTo('#partners')">
          {{ $t("solutionSection.educationalPartners.learnMore") }}
        </button>
      </div>
      <div :class="$style.placeholder">picture/slider</div>
    </div>
    <div :class="$style.schoolGardensBlock">
      <div :class="$style.placeholder">picture/slider</div>
      <div :class="$style.featureText">
        <div :class="$style.subtitle">
          {{ $t("solutionSection.modelCities.title") }}
        </div>
        <div :class="$style.text">
          <p>{{ $t("solutionSection.modelCities.text") }}</p>
        </div>
        <button :class="$style.button" @click="scrollTo('#start')">
          {{ $t("solutionSection.modelCities.learnMore") }}
        </button>
      </div>
    </div>
    <div :class="$style.content">
      <div :class="$style.workBlock">
        <Applicate :class="$style.applicate" />
        <div :class="$style.item">
          <div :class="$style.subtitle">
            {{ $t("solutionSection.first.title") }}
          </div>
          <div :class="$style.text">
            {{ $t("solutionSection.first.text") }}
          </div>
          <div :class="$style.subtext">
            <div :class="$style.subtextTitle">
              {{ $t("solutionSection.first.firstItem.title") }}
            </div>
            <div>
              {{ $t("solutionSection.first.firstItem.text") }}
            </div>
          </div>
          <div :class="$style.subtext">
            <div :class="$style.subtextTitle">
              {{ $t("solutionSection.first.secondItem.title") }}
            </div>
          </div>
        </div>
      </div>

      <div :class="[$style.workBlock, $style.reverse]">
        <div :class="$style.item">
          <div :class="$style.subtitle">
            {{ $t("solutionSection.second.title") }}
          </div>
          <div :class="$style.text">
            {{ $t("solutionSection.second.subtext") }}
          </div>
        </div>
        <div :class="$style.image">
          <img src="/images/solution/1-horizontal.png" alt="" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Applicate from "./Applicate.vue";
import VueScrollTo from "vue-scrollto";
export default {
  components: {
    Applicate,
  },
  methods: {
    scrollTo(component) {
      VueScrollTo.scrollTo(component, {
        offset: -50,
        duration: 500,
      });
    },
  },
};
</script>

<style lang="scss" module>
.container {
  @include container;
  @include custom(720) {
    margin-bottom: 4rem;
  }
  .title {
    @include F64-900;
    margin: 0 0 2rem 0;
    text-align: center;
    @include custom(1050) {
      margin: 0 0 3rem 0;
    }
    @include custom(830) {
      font-size: 3rem;
      line-height: 100%;
    }
    @include mobile {
      font-size: 2.8rem;
    }
  }
  .description {
    @include F28-400;
    max-width: 70rem;
    margin: 0 auto 6.25rem auto;
    text-align: center;
    @include custom(1050) {
      margin-bottom: 3rem;
      font-size: 1.5rem;
      line-height: 120%;
    }
    @include custom(530) {
      font-size: 1.1rem;
    }
  }
  .schoolGardensBlock {
    display: grid;
    grid-template-columns: minmax(18rem, 0.9fr) minmax(0, 1fr);
    align-items: center;
    gap: 4rem;
    margin: 0 0 6.25rem 0;
    @include custom(1050) {
      gap: 2rem;
      margin-bottom: 4rem;
    }
    @include custom(760) {
      grid-template-columns: 1fr;
      gap: 2rem;
    }
    &.reverse {
      grid-template-columns: minmax(0, 1fr) minmax(18rem, 0.9fr);
      @include custom(760) {
        grid-template-columns: 1fr;
      }
    }
    &.reverse .placeholder {
      @include custom(760) {
        order: 1;
      }
    }
    &.reverse .featureText {
      @include custom(760) {
        order: 2;
      }
    }
    .placeholder {
      @include F28-600;
      width: 100%;
      aspect-ratio: 1 / 1;
      max-width: 36rem;
      margin: 0 auto;
      border-radius: 0.625rem;
      background-color: #d9d9d9;
      color: $black;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      @include custom(530) {
        font-size: 1.25rem;
      }
    }
    .featureText {
      .subtitle {
        @include F36-600;
        line-height: 2.75rem;
        margin: 0 0 1.5rem 0;
        @include custom(1200) {
          font-size: 2rem;
          margin: 0 0 1rem 0;
        }
        @include custom(870) {
          font-size: 1.8rem;
        }
        @include custom(450) {
          font-size: 1.5rem;
          line-height: 100%;
          margin: 0 0 1rem 0;
        }
      }
      .text {
        @include F28-400;
        margin-bottom: 1.5rem;
        @include custom(1200) {
          font-size: 1.75rem;
          line-height: 120%;
        }
        @include custom(1050) {
          font-size: 1.5rem;
        }
        @include custom(530) {
          font-size: 1.1rem;
        }
        & p {
          margin: 0 0 1.5rem 0;
          &:last-child {
            margin: 0;
          }
        }
      }
      .button {
        @include F28-600;
        display: inline-flex;
        align-items: center;
        justify-content: center;
        padding: 1rem 2rem;
        border: 0.3125rem solid $orange;
        border-radius: 0.625rem;
        background-color: $white;
        color: $black;
        cursor: pointer;
        transition: all 0.3s ease-in-out;
        &:hover {
          background-color: $orange;
          color: $white;
        }
        @include custom(530) {
          width: 100%;
          font-size: 1.25rem;
        }
      }
    }
  }
  .content {
    .workBlock {
      display: grid;
      grid-template-columns: minmax(18rem, 0.9fr) minmax(0, 1fr);
      align-items: center;
      gap: 4rem;
      margin: 0 0 6.25rem 0;
      @include custom(1050) {
        gap: 2rem;
        margin-bottom: 4rem;
      }
      @include custom(760) {
        grid-template-columns: 1fr;
        gap: 2rem;
      }
      .applicate {
        max-width: 36rem;
        margin: 0 auto;
        width: 100%;
      }
      &.reverse {
        grid-template-columns: minmax(0, 1fr) minmax(18rem, 0.9fr);
        @include custom(760) {
          grid-template-columns: 1fr;
        }
      }
      &.reverse .image {
        @include custom(760) {
          order: 1;
        }
      }
      &.reverse .item {
        @include custom(760) {
          order: 2;
        }
      }
      .image {
        width: 100%;
        max-width: 36rem;
        margin: 0 auto;
        & img {
          width: 100%;
          height: auto;
          display: block;
        }
      }
      .item {
        .subtitle {
          @include F36-600;
          line-height: 2.75rem;
          margin: 0 0 1.5rem 0;
          @include custom(1200) {
            font-size: 2rem;
            margin: 0 0 1rem 0;
          }
          @include custom(870) {
            font-size: 1.8rem;
          }
          @include custom(450) {
            font-size: 1.5rem;
            line-height: 100%;
            margin: 0 0 1rem 0;
          }
        }
        .text {
          @include F28-400;
          margin-bottom: 1.5rem;
          @include custom(1200) {
            font-size: 1.75rem;
            line-height: 120%;
          }
          @include custom(1050) {
            font-size: 1.5rem;
          }
          @include custom(530) {
            font-size: 1.1rem;
          }
        }
        .subtext {
          margin-bottom: 1.5rem;
          @include F28-400;
          font-size: 1.35rem;
          line-height: 150%;
          @include custom(530) {
            font-size: 1.1rem;
            line-height: 120%;
          }
          .subtextTitle {
            @include F32-600;
            font-size: 1.5rem;
            margin: 0 0 0.5rem 0;
            @include custom(530) {
              font-size: 1.25rem;
            }
          }
        }
      }
    }
  }
}
</style>
