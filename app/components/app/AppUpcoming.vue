<template>
<section class="app-upcoming">
  <div class="app-upcoming__wrapper">
    <div class="app-upcoming__container">
      <h2 class="app-upcoming__title section-title">
        Мероприятия
    </h2>

    <TheSwiper :component="EventCard" :list="list" class="app-upcoming__swiper"/>

      <!-- <div class="app-upcoming__swiper">
      <EventCard
        v-for="card in [list[0]]"
        :key="card.slug"
        :data="card"
        class="app-listing__card"
      />
      </div> -->

    <a href="#" class="app-upcoming__link link">Смотреть все</a>
  </div>
    </div>
</section>
</template>

<script setup>

 import { EventCard } from "#components";
 
   const list = ref([]);

  const URL = "http://localhost:3000/json/events.json";

  const { data } = await useAsyncData(`upcoming`, () => {
    return $fetch(URL);
  });
  if (data?.value) list.value = data.value;
</script>

<style lang="less">
.app-upcoming {
    position: relative;
    width: 100%;
    padding: 35px 0;
    overflow: hidden;
    &::before,
    &::after {
        content: "";
        display: block;
        position: absolute;
        top: 0;
        width: 0;
        height: 0;
        border-bottom: 35px solid fade(@white, 60%);
    }
    &::before {
        left: 0;
        border-right: 34vw solid transparent;
    }
    &::after {
        right: 0;
        border-left: 66vw solid transparent;
    }
    &__wrapper {
        width: 100%;
        padding: 90px 0;
        background-color: fade(@white, 60%);
         &::before,
         &::after {
            content: "";
            display: block;
            position: absolute;
            bottom: 0;
            border-top: 35px solid fade(@white, 60%);
        }
         &::before {
        left: 0;
        border-right: 60vw solid transparent;
    }
        &::after {
        right: 0;
        border-left: 39vw solid transparent;
    }
    }

    &__container {
    .container();
    display: flex;
    flex-direction: column;
    }
    &__link {
    .container();
    color: @black;
    display: flex;
    flex-direction: row;
    justify-content: flex-end;
    text-decoration: none;
    font-family: @font1;
    font-size: 16px;
    font-weight: 600;
    line-height: 22px;
    align-items: center;
}
}
</style>