<template>
  <div :class="$style.container">
    <div :class="$style.row">
      <div :class="$style.text">
        <div :class="$style.title">{{ $t("aboutSection.firstTitle") }}</div>
        <div :class="$style.subtext">
          {{ $t("aboutSection.firstText") }}
        </div>
      </div>
      <div :class="$style.image">
        <img src="/images/about/1.png" alt="" />
      </div>
    </div>
    <div :class="$style.row">
      <div :class="$style.image">
        <img src="/images/about/2.png" alt="" />
      </div>
      <div :class="$style.text">
        <div :class="$style.title" id="goal">
          {{ $t("aboutSection.secondTitle") }}
        </div>
        <div :class="$style.subtext">
          {{ $t("aboutSection.secondText") }}
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" module>
.container {
  @include container;
  .row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 3rem;
    @include custom(800) {
      margin: 0 0 5rem 0;
    }
    @include custom(530) {
      margin: 0 0 4rem 0;
      gap: 1.5rem;
    }
    @include custom(375) {
      margin: 0 0 2rem 0;
    }
    @include mobile {
      flex-direction: column;
      gap: 0;
    }
    &:nth-child(2) {
      @include custom(800) {
        margin: 0 0 10rem 0;
      }
      @include custom(530) {
        margin: 0 0 6rem 0;
      }
      @include mobile {
        margin: 0 0 4rem 0;
      }
      @include custom(375) {
        margin: 0 0 2rem 0;
      }
      .image {
        @include mobile {
          order: 1;
          margin: 0 0 4rem 0;
        }
      }
    }
    .text {
      .title {
        @include F64-900;
        margin: 0 0 2.25rem 0;
        @include custom(1000) {
          font-size: 2.5rem;
          margin: 0 0 0 0;
        }
        @include custom(530) {
          font-size: 2rem;
        }
      }
      .subtext {
        max-width: 45rem;
        @include F28-400;
        @include custom(1000) {
          font-size: 1.5rem;
          line-height: 100%;
        }
        @include custom(530) {
          font-size: 1.1rem;
          line-height: 120%;
        }
      }
      @include mobile {
        order: 2;
      }
    }
    .image {
      max-width: 26rem;
      max-height: 32rem;
      @include custom(800) {
        max-width: 14rem;
        max-height: 16rem;
      }
      @include mobile {
        order: 1;
        margin: 0 0 2rem 0;
      }
      & img {
        width: 100%;
        height: 100%;
      }
    }
  }
}
</style>
