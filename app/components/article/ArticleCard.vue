<template>
  <article class="article-card">
    <a href="#" class="article-card__link">
      <picture class="article-card__picture">
        <source
          type="image/webp"
          media="(max-width: 450px)"
          :srcset="data.img_webp"
        />
        <source media="(max-width: 450px)" :srcset="data.img" />

        <source
          type="image/webp"
          media="(max-width: 1169px)"
          :srcset="data.img_tablet_webp"
        />
        <source media="(max-width: 1169px)" :srcset="data.img_tablet" />

        <source type="image/webp" :srcset="data.img_webp" />
        <img :src="data.img" :alt="data.alt" class="article-card__img" />
      </picture>
    </a>
    <div class="article-card__info">
      <time :datetime="data.date" class="article-card__time">
        {{ date }}
      </time>
      <a href="#" class="article-card__title-link">
        <h4 class="article-card__title">
          {{ data.title }}
        </h4>

        <div class="article-card__arrow arrow">
          <SvgIcon name="arrow" class="arrow__icon" width="92" height="62" />
        </div>
      </a>
      <p class="article-card__description">
        {{ data.description }}
      </p>
    </div>
  </article>
</template>

<script setup>
const props = defineProps({
  data: {
    type: Object,
    default: () => ({}),
  },
});

const date = computed(() => {
  try {
    return new Date(props.data.date).toLocaleDateString();
  } catch {
    return null;
  }
});
</script>

<style lang="less">
.article-card {
  box-sizing: border-box;
  position: relative;
  display: flex;
  width: 100%;
  @media @bw1170 {
    flex-direction: column;
    max-width: 708px;
  }
  //   @media @bw768 {
  //     // max-width: 708px;
  //     justify-content: center;
  //   }
  //   @media @bw451 {
  //     justify-content: center;
  //     max-width: 100%;
  //   }

  &:active {
    .article-card__picture {
      box-shadow: 0 0 30px fade(@black, 55%);
    }
  }
  &:hover {
    @media (hover: hover) {
      .article-card__picture {
        box-shadow: 0 0 30px fade(@black, 55%);
      }
    }
  }
  & + .article-card {
    margin-top: 120px;
    &::before {
      content: "";
      display: block;
      position: absolute;
      margin: 0 auto 60px;
      bottom: 100%;
      left: 0;
      right: 0;
      width: 100%;
      max-width: 1255px;
      height: 1px;
      background-color: @black;
      pointer-events: none;
      @media @bw1170 {
        margin-bottom: 50px;
      }
      @media @bw500 {
        margin-bottom: 40px;
      }
    }
  }
  &__link {
    flex-shrink: 0;
    align-self: flex-start;
    display: block;
    width: 467px;
    margin-right: 60px;
    font-size: 0;
    text-decoration: none;
    @media @bw1660 {
      margin-right: 40px;
    }
    @media @bw1340 {
      margin-right: 30px;
    }
    @media @bw1170 {
      width: 100%;
      margin-right: 0;
    }
    &:active {
      & ~ .article-card__info {
        .article-card__title-link {
          color: @red;
          text-decoration-color: @red;
        }
      }
    }
    &:hover {
      @media (hover: hover) {
        & ~ .article-card__info {
          .article-card__title-link {
            color: @red;
            text-decoration-color: @red;
          }
        }
      }
    }
  }

  &__picture {
    display: block;
    position: relative;
    width: 100%;
    transition: box-shadow 0.2s;
    overflow: hidden;
    &::after {
      content: "";
      display: block;
      width: 100%;
      padding-top: 62.3126%;
    }
  }

  &__img {
    // max-width: 870px;
    // height: auto;
    // box-sizing: border-box;
    // margin: 0;
    display: block;
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    // @media @bw1170 {
    //   max-width: 100%;
    // }
    // @media @bw768 {
    //   max-width: 100%;
    //   // padding-right: 50px;
    // }
    // @media @bw451 {
    //   max-width: 100%;
    // }
  }
  &__info {
    box-sizing: border-box;
    position: relative;
    display: flex;
    flex-direction: column;
    width: 100%;
    padding-top: 30px;
    padding-bottom: 30px;
    padding: 30px 0;
    padding-right: 150px;
    @media @bw1660 {
      padding-right: 130px;
    }
    @media @bw1340 {
      padding-right: 95px;
    }
    @media @bw1170 {
      padding-top: 0;
      padding-bottom: 0;
    }
    @media @bw500 {
      padding-right: 0;
      padding-bottom: 60px;
    }
    @media @bw451 {
      //  display: block;
      height: auto;
      margin: 0 auto;
    }
  }

  &__time {
    color: @black;
    margin: 0 0 40px;
    font-weight: 300;
    font-size: 16px;
    line-height: 22px;
    letter-spacing: 0%;
    @media @bw1170 {
      margin: 25px 0 0;
    }
    @media @bw500 {
      margin-top: 10px;
      font-size: 14px;
      line-height: 19px;
    }
  }

  &__title-link,
  &__description {
    max-width: 470px;
  }

  &__title-link {
    margin: auto 0 40px;
    color: @black;
    text-decoration-color: transparent;
    transition:
      color 0.2s,
      text-decoration-color 0.2s;
    &:hover {
      color: @red;
      text-decoration-color: @red;
    }
  }

  &__title {
    margin: 0;
    color: inherit;
    font-weight: 600;
    font-size: 24px;
    line-height: 33px;
  }

  &__description {
    margin: 0;
    font-size: 16px;
    line-height: 22px;
    @media @bw500 {
      font-size: 14px;
      line-height: 19px;
    }
  }

  &__arrow {
    position: absolute;
    right: 0;
    bottom: 30px;
    color: inherit;
    transition: none;
    @media @bw1170 {
      bottom: 0;
    }
    &:hover {
      color: @red;
    }
    &__icon {
      width: 100%;
      height: 100%;
    }
  }
}
</style>
