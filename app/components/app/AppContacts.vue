<template>
  <section class="app-contacts">
    <h2 class="app-contacts__title section-title">Контакты</h2>

    <div class="app-contacts__wrapper">
      <ul class="app-contacts__list">
        <li class="app-contacts__item">
          <div class="app-contacts__item-mark">
            <SvgIcon
              class="app-contacts__item-icon"
              width="18"
              height="18"
              name="location"
            />
          </div>
          <div class="app-contacts__item-content">
            <h4 class="app-contacts__item-title">Томск, Красноармейская 146</h4>

            <div class="app-contacts__item-info">2 этаж</div>

            <div class="contacts__item-info">оф. 206</div>
          </div>
        </li>

        <li class="app-contacts__item">
          <div class="app-contacts__item-mark">
            <SvgIcon
              class="app-contacts__item-icon"
              width="18"
              height="21"
              name="home"
            />
          </div>
          <div class="app-contacts__item-content">
            <h4 class="app-contacts__item-title">Отдел аренды</h4>

            <a href="tel:+73822907256" class="app-contacts__item-info">
              8 (3822) 90-72-56
            </a>

            <a href="mailto:idat@tusur.ru" class="app-contacts__item-info">
              idat@tusur.ru
            </a>
          </div>
        </li>

        <li class="app-contacts__item">
          <div class="app-contacts__item-mark">
            <SvgIcon
              class="app-contacts__item-icon"
              width="21"
              height="20"
              name="star"
            />
          </div>
          <div class="app-contacts__item-content">
            <h4 class="app-contacts__item-title">Отдел мероприятий</h4>

            <a href="tel:+73822907256" class="app-contacts__item-info">
              8 (3822) 90-72-56
            </a>

            <a href="mailto:idat@tusur.ru" class="app-contacts__item-info">
              idat@tusur.ru
            </a>
          </div>
        </li>
      </ul>

      <div class="app-contacts__map" id="js-app-contactsMap"></div>
    </div>

  </section>
</template>

<script setup></script>

<style lang="less">
.app-contacts {
  .container;
  
  &__wrapper {
    display: flex;
    align-items: center;
    @media @bw1020 {
      flex-direction: column;
    }
  }
  &__list {
    flex-shrink: 0;
    width: 400px;
    margin: 0 30px 0 0;
    padding: 0;
    list-style: none;
    @media @bw1020 {
      order: 1;
      width: 100%;
      margin: 0;
      display: flex;
      align-items: flex-start;
    }
    @media @bw768 {
      flex-direction: column;
    }
  }
  &__item {
    box-sizing: border-box;
    display: flex;
    align-items: center;
    margin: 0 0 65px;
    @media @bw1020 {
      flex-direction: column;
      width: 33.3333%;
      margin: 0;
      padding: 0 10px;
    }
    @media @bw768 {
      flex-direction: row;
      align-items: flex-start;
      width: 100%;
      margin: 0 0 45px;
      padding: 0;
    }
    &:last-child {
      margin: 0;
    }
  }
  &__item-mark {
    flex-shrink: 0;
    display: flex;
    margin-right: 55px;
    width: 110px;
    height: 110px;
    background: @black;
    color: @red;
    @media @bw1340 {
      margin-right: 30px;
    }
    @media @bw1020 {
      margin: 0 0 30px;
    }
    @media @bw768 {
      margin: 0 30px 0 0;
      width: 65px;
      height: 65px;
    }
  }

  &__item-icon {
    margin: auto;
    min-width: 110px;
    min-height: 110px;
  }
  

  &__item-content {
    display: flex;
    flex-direction: column;
    @media @bw1020 {
      align-items: center;
      text-align: center;
    }
    @media @bw768 {
      align-items: flex-start;
      text-align: left;
    }
  }

  &__item-title {
    margin: 0 0 10px;
    font-weight: 600;
    font-size: 20px;
    line-height: 27px;
    @media @bw1020 {
      font-size: 18px;
      line-height: 25px;
    }
    @media @bw768 {
      font-size: 14px;
      line-height: 19px;
    }
  }
  &__item-info {
    margin: 0 0 5px;
    font-size: 16px;
    line-height: 22px;
    @media @bw768 {
      margin: 0;
      font-size: 14px;
      line-height: 19px;
    }
    &[href] {
      text-decoration: none;
      transition: color 0.2;
      &:active {
        color: @red;
      }
      &:hover {
        @media (hover: hover) {
          color: @red;
        }
      }
    }
    &:last-child
    {
      margin: 0;
    }
  }

  &__map {
    width: 750px;
    height: 490px;
    margin-left: auto;
    @media @bw1020 {
      width: 100%;
      height: 465px;
      margin-bottom: 125px;
    }
    @media @bw768 {
      margin-bottom: 65px;
    }
  }
}
</style>
