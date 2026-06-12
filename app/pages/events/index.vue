<template>
  <div class="events">
    <AppListing 
    v-slot="{ list }"
    class="events__listing" 
    :title="'Мероприятия'"
    :moreBtn="true"
    :url="'http://localhost:3000/json/events.json'"
    >
      <EventCard
        v-for="card in list"
        :key="card.slug"
        :data="card"
        class="app-listing__card"
      />
    </AppListing>

    <AppServices class="events__services" />

    <AppOffers class="events__offers" />

    <AppEvents class="events__events" />

  </div>
</template>

<script setup></script>

<style lang="less">
.events {
  padding: 140px 0 100px;
  @media @bw1340 {
    padding: 90px 0 100px;
  }
  @media @bw768 {
    padding: 80px 0 100px;
  }
  &__listing {
    margin-bottom: 100px;
  }
  &__services {
    margin-bottom: 50px;
    flex-direction: column;
  }

  &__offers {
    margin-bottom: 100px;
    @media @bw768 {
      margin-bottom: 90px;
    }
  }
}
</style>
