<template>
  <div class="app-events__wrapper">
    <ul class="app-events__list">
      <li class="app-events__item-prices">
        <div class="app-events__item-mark">
          <SvgIcon
            class="app-events__item-icon"
            width="18"
            height="18"
            name="location"
          />
        </div>
        <div class="app-events__item-content">
          <h4 class="app-events__item-title">Цены</h4>
          <br />
          <span class="app-events__item-info">
            Цены, указанные на сайте носят информационный характер. Мы
            придерживаемся индивидуального подхода в работе с клиентом.
          </span>
        </div>
      </li>

      <li class="app-events__item-contacts">
        <div class="app-events__item-mark">
          <SvgIcon
            class="app-events__item-icon"
            width="18"
            height="21"
            name="contact"
          />
        </div>

        <div class="app-events__item-content">
          <h4 class="app-events__item-title">Контакты</h4>

          <span class="app-events__item-p">Отдел организации мероприятий</span>

          <div class="app-events__item-number">
            <a class="app-events__item-number" href="tel:+73822907256"
              >8 (3822) 90-72-56
            </a>
          </div>

          <div class="app-events__item-email">
            <a class="app-events__item-email" href="mailto:idat@tusur.ru"
              >idat@tusur.ru</a
            >
          </div>
        </div>
      </li>

      <li class="app-events__item-advantage">
        <div class="app-events__item-mark">
          <SvgIcon
            class="app-events__item-icon"
            width="18"
            height="21"
            name="handshake"
          />
        </div>
        <div class="app-events__item-content">
          <h4 class="app-events__item-title">Преимущество</h4>
          <br />
          <span class="app-events__item-info">
            Мы имеем все возможности для того, чтобы помочь как малому бизнесу и
            молодым талантам, так и большим корпорациям и холдингам.
          </span>
        </div>
      </li>
    </ul>
  </div>
</template>

<script setup></script>

<style lang="less">
.app-events {
  .container;
  &__list {
    .container;
    align-items: baseline;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: auto;
    gap: 100px;
    margin: 0 auto 150px;
    list-style: none;
    @media @bw1170 {
      gap: 10px;
    }
    @media @bw960 {
      gap: 20px;
      grid-template-columns: repeat(2, 1fr);
      grid-template-rows: auto auto;
      justify-content: center;
      align-content: center;
    }
    @media @bw600 {
      grid-template-columns: 1fr;
      grid-template-rows: auto;
      grid-template-areas:
        "item-price"
        "item-contact"
        "item-advantage";
      gap: 40px;
    }
  }

  &__item {
    margin-bottom: 67px;
    display: grid;
    grid-template-rows: auto 1fr;
    justify-items: center;
    @media @bw370 {
      gap: 15px;
    }
  }
  &__item-content {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  &__item-title {
    flex-shrink: 0;
    width: 100%;
    height: 27px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    color: @black;
    font-family: @font1;
    font-size: 20px;
    font-weight: 600;
    line-height: 27px;
    letter-spacing: 0%;
    text-align: center;
    @media @bw1340 {
      width: 293px;
      font-size: 20px;
    }
    @media @bw768 {
      margin-top: 30px;
      margin-bottom: 0px;
      width: 280px;
      height: 57px;
      line-height: 25px;
      font-size: 18px;
      font-weight: 700;
    }
    @media @bw370 {
      margin-top: 30px;
      margin-bottom: 10px;
      width: 185px;
      height: 19px;
      font-size: 14px;
      line-height: 19px;
      font-weight: 600;
    }
  }
  &__item-info {
    width: 100%;
    height: 22px;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    margin-bottom: 5px;
    color: @black;
    font-family: @font1;
    font-size: 16px;
    font-weight: 400;
    line-height: 22px;
    letter-spacing: 0%;
    text-align: center;
    text-decoration: none;
    @media @bw600 {
      margin-bottom: 40px;
      width: 224px;
      font-size: 13px;
      line-height: 19px;
    }
  }
  &__item-mark {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  &__item-icon {
    width: 47px;
    height: 47px;
    min-width: 110px;
    min-height: 110px;
    object-fit: contain;
    @media @bw370 {
      max-width: 65px;
      height: 65px;
      object-fit: contain;
    }
  }
  &__item-price {
    @media @bw960 {
      grid-column: 1 / 2;
      grid-row: 1 / 2;
    }
    @media @bw600 {
      grid-area: item-price;
    }
  }
  &__item-contact {
    @media @bw960 {
      grid-column: 2 / 3;
      grid-row: 1 / 2;
    }
    @media @bw600 {
      grid-area: item-contacts;
    }
  }

  &__item-advantage {
    @media @bw960 {
      grid-column: 1 / 3;
      grid-row: 2 / 3;
    }
    @media @bw600 {
      grid-area: item-advantage;
    }
  }

  &__item-p,
  &__item-number,
  &__item-email {
    width: 100%;
    height: 22px;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    color: @black;
    font-family: @font1;
    font-size: 16px;
    font-weight: 400;
    line-height: 22px;
    letter-spacing: 0%;
    text-align: center;
    text-decoration: none;
    cursor: pointer;
    @media @bw600 {
      width: 224px;
      font-size: 13px;
      line-height: 19px;
    }
  }
  &__item-number,
  &__item-email {
    cursor: pointer;
  }
}
</style>
