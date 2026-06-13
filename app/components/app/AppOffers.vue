<template>
  <section class="app-offers">
    <h4 class="app-offers__title">Я ХОЧУ:</h4>

    <div class="app-offers__btns">
      <button
        type="button"
        class="app-offers__btn btn btn--red"
        @click="openPopup()"
      >
        Провести мероприятие
      </button>

      <button type="button" class="app-offers__btn btn">
        Стать арендатором
      </button>
    </div>

    <ModalWindow
      alive
      :name="'getOffer'"
      :title="' Заполните форму<br />и мы подберем площадку'"
    ></ModalWindow>
  </section>
</template>

<script setup>

 const store = useStore();
  const openPopup = () => {
    store.openModal("getOffer");
  };
</script>

<style lang="less">
.app-offers {
  .container;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  &__title {
    text-align: center;
    margin-bottom: 46px;
    font-size: 22px;
    font-weight: 400;
    font-family: @font2;
    width: 100%;
    max-width: 624px;
    line-height: 30px;
    letter-spacing: 2%;
    text-transform: uppercase;
    @media @bw768 {
      font-size: 16px;
      line-height: 20px;
    }
    @media @bw370 {
      font-size: 13px;
      line-height: 17px;
    }
  }
  &__btns {
    max-width: 100%;
    display: flex;
    align-items: center;
    gap: 106px;
    cursor: pointer;
    @media @bw1340 {
      gap: 94px;
    }
    @media @bw768 {
      justify-content: center;
      gap: 56px;
      flex-wrap: wrap;
    }
    @media @bw600 {
      gap: 25px;
      flex-wrap: wrap;
    }
  }

  &__btn {
    width: 280px;
    height: 49px;
  }
}
</style>
