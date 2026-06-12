<template>
  <article class="event">
    <header class="event__header">
      <h1 class="event__title title">{{ data.title }}</h1>

      <div class="event__about">
        <div class="event__info">
          <time v-if="datetime" :datetime="data.date" class="event__time">
            {{ datetime.date }}
          </time>
          <div class="event__info-text">{{ data.location }}</div>
        </div>

        <picture class="event__picture">
          <source type="image/webp" :srcset="data.img_webp" />

          <img :src="data.img" :alt="data.alt" class="event__image" />
        </picture>

        <div class="event__info">
          <span v-if="datetime" class="event__time" data-caption="начало">
            {{ datetime.time }}
          </span>
          <div class="event__info-text">{{ data.address }}</div>
        </div>
      </div>
    </header>

    <div class="event__container">
      <div class="content event__content" v-html="data.content"></div>
    </div>
  </article>
</template>

<script setup>
const slug = computed(() => useRoute().params.event);
const URL = computed(
  () => `http://localhost:3000/json/events/${slug.value}.json`,
);

const { data } = await useFetch(URL);

const datetime = computed(() => {
  try {
    const date = new Date(data.value.date);
    return {
      date: date.toLocaleDateString(),
      time: date.toLocaleTimeString("ru-RU", {
        hour: "2-digit",
        minute: "2-digit",
      }),
    };
  } catch {
    return null;
  }
});
</script>

<style lang="less">
.event {
  padding: 40px 0 150px;
  //  box-sizing: border-box;
  //   display: flex;
  //   flex-direction: column;
  //   width: 100%;
  //   max-width: 1414px;
  //   margin: 0 auto;
  //   padding-left: 40px;
  //   padding-right: 40px;
  @media @bw768 {
    padding: 80px 0 100px;
  }
  &__header {
    .container;
    margin-bottom: 80px;
  }

  &__container {
    .container;
  }
  &__about {
    display: flex;
    gap: 40px;
    align-items: center;
    justify-content: center;
    flex-wrap: nowrap;
    flex-direction: row;
  }
  &__title {
    text-align: center;
    margin-bottom: 80px;
    color: @black;
    font-family: @font2;
    font-style: Medium;
    font-size: 70px;
    font-weight: 500;
    line-height: 90px;
    letter-spacing: 0%;
    @media @bw768 {
      font-size: 40px;
      line-height: 51px;
      margin-bottom: 64px;
    }
    @media @bw500 {
      font-size: 25px;
      line-height: 36px;
      margin-bottom: 40px;
    }
    @media @bw370 {
      font-size: 20px;
      line-height: 26px;
      margin-bottom: 40px;
    }
  }

  &__picture {
    object-fit: cover;
    max-width: 506px;
    width: 506px;
    // height: 532px;
    @media @bw1340 {
      width: 426px;
    }
    @media @bw1170 {
      width: 426px;
    }
    @media @bw1020 {
      width: 426px;
    }
    @media @bw768 {
      width: 245px;
    }
  }
  &__info-text {
    display: flex;
    align-items: center;
    justify-content: center;
    color: @black;
    font-family: @font3;
    font-size: 40px;
    font-weight: 500;
    @media @bw1170 {
      width: 123px;
    }
  }

  &__time {
    display: flex;
    align-items: center;
    justify-content: center;
    color: @black;
    font-family: @font3;
    font-size: 40px;
    font-weight: 500;
    @media @bw1170 {
      width: 133px;
    }
  }
}
</style>
