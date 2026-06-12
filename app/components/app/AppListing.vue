<template>
  <section class="app-listing">
    <h1 class="app-listing__title section-title">{{ title }}</h1>

    <div :class="listClass">
      <slot :list="list" />
    </div>

    <button v-if="moreBtn" type="button" class="more-btn app-listing__more-btn">
      Показать всё

      <SvgIcon class="more-btn__arrow" name="arrow_down" width="62" height="92" />
    </button>

    <a v-else-if="moreLink" href="#" class="app-listing__link link">Смотреть все</a>

  </section>
</template>

<script setup>
const props = defineProps({
  title: {
    type: String,
    default: "",
  },
  url: {
    type: String,
    default: "",
    required: true,
  },
  moreBtn: {
    type: Boolean,
    default: false
  },
    moreLink: {
    type: Boolean,
    default: false
  },
  grid: {
    type: String,
    default: "row",
  },
});

const listClass = computed(() => props.grid === "column" ? "app-listing__column-list" : "app-listing__list")

const list = ref([]);

const { data } = props.url
  ? await useAsyncData(`list-${props.url}`, () => {
      return $fetch(props.url);
    })
  : { data: null };

if (data?.value) list.value = data.value;
</script>

<style lang="less">
.app-listing {
  .container;
  display: flex;
  flex-direction: column;

  &__column-list {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  &__list {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin: 0 -33px -120px;

    @media @bw1660 {
      margin: 0 -20px -100px;
    }

    @media @bw1340 {
      margin: 0 -15px -100px;
    }

    @media @bw1020 {
      justify-content: center;
      margin: 0 -15px -80px;
    }

    @media @bw768 {
      margin: 0 -10px -80px;
    }

    @media @bw650 {
      margin: 0 0 -60px;
    }
  }
  &__card {
    width: calc(33.3333% -58px);
    margin: 0 30px 120px;
    @media @bw1660 {
      width: calc(33.3333% -40px);
      margin: 0 20px 100px;
    }
    @media @bw1340 {
      width: calc(33.3333% -30px);
      margin: 0 15px 100px;
    }

    @media @bw1020 {
      width: calc(50% -30px);
      max-width: 405px;
      margin: 0 15px 80px;
    }

    @media @bw768 {
      margin: 0 10px 80px;
    }

    @media @bw650 {
      width: 100%;
      margin: 0 0 60px;
      max-width: 500px;
    }
  }
  // &__link {
  //   color: @black;
  //   display: flex;
  //   flex-direction: row;
  //   justify-content: flex-end;
  //   margin-top: 100px;
  //   text-decoration: none;
  //   font-family: @font1;
  //   font-size: 16px;
  //   font-weight: 600;
  //   line-height: 22px;
  //   align-items: center;
  //   @media @bw1170 {
  //     box-sizing: border-box;
  //   }
  // }
  // &__link1 {
  //   color: @black;
  //   display: flex;
  //   flex-direction: row;
  //   justify-content: flex-end;
  //   margin-top: 60px;
  //   text-decoration: none;
  //   font-family: @font1;
  //   font-size: 16px;
  //   font-weight: 600;
  //   line-height: 22px;
  //   align-items: center;
  //   @media @bw1170 {
  //     box-sizing: border-box;
  //   }
  // }
  // &__more-btn {
  //   display: flex;
  //   flex-direction: column;
  //   align-items: center;
  //   color: @black;
  //   font-weight: 600;
  //   font-size: 16px;
  //   line-height: 22px;
  //   transition: color 0.2s;
  //   text-decoration: none;
  //   cursor: pointer;
  //   background: none;
  //   border: none;
  //   gap: 20px;
  //   @media @bw768 {
  //     font-size: 14px;
  //     line-height: 19px;
  //   }
  //   &:active {
  //     color: @red;
  //   }
  //   &:hover {
  //     @media (hover: hover) {
  //       color: @red;
  //     }
  //   }
  // }
  // &__arrow {
  //   // margin-top: 15px;
  //   // @media @bw1340 {
  //   //     width: 40px;
  //   //     height: 67px;
  //   // }
  //   transform: rotate(90deg);
  //   display: flex;
  //   align-items: center;
  //   justify-content: center;
  //   color: inherit;
  //   transition: none;
  // }

  &__link {
    margin-top: 85px;
    margin-left: auto;
    @media @bw1660 {
      margin-top: 75px;
    }
    @media @bw1340 {
      margin-top: 55px;
    }
    @media @bw768 {
      margin-top: 45px;
    }
  }
  &__more-btn {
    margin: 70px auto 0;
    @media @bw1660 {
      margin-top: 60px;
    }
  }
}
</style>
