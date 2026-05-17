<template>
  <footer class="page-footer">
    <div class="page-footer__top-lines"></div>

    <div class="page-footer__wrapper">
      <nav class="page-footer__nav">
        <a href="#" class="page-footer__nav-link">Календарь мероприятий</a>
        <a href="#" class="page-footer__nav-link">Провести мероприятие</a>
        <a href="#" class="page-footer__nav-link">Стать арендатором</a>
        <a href="#" class="page-footer__nav-link">Наши проекты</a>
        <a href="#" class="page-footer__nav-link">Контакты</a>
      </nav>

      <SubscribeForm class="page-footer__subscribe-form" />
    </div>

    <div class="page-footer__vault">
      <div class="page-footer__terms">
        <div class="page-footer__copyrights">© Millennials {{ new Date().getFullYear() }}</div>

        <div class="page-footer__terms-links">
          <a href="#" class="page-footer__terms-link"
            >Политика конфиденциальности</a
          >
          <a href="#" class="page-footer__terms-link">Cookies</a>
        </div>
      </div>

      <AppSocials class="page-footer__socials" />

      <div class="page-footer__Dignity">
        <a href="#" class="page-footer__Dignity-icon"> Создание и продвижение </a>
        <SvgIcon
          class="app-socials__Dignity-icon"
          width="80"
          height="35"
          name="Dignity"
        />
      </div>
    </div>
  </footer>
</template>

<script setup></script>

<style lang="less">
.page-footer {
  position: relative;
  max-width: 1414px;
  width: 100%;
  margin: 0 auto;
  padding: 40px 0;
  background-color: transparent;
  display: grid;
  grid-template-columns: 1fr 385px;
  grid-template-rows: auto auto;
  grid-template-areas:
    "nav subscribe"
    "vault vault";
  @media @bw700 {
    gap: 80px;
  }
  @media @bw650 {
    gap: 50px;
    grid-template-columns: 1fr auto;
  }
  @media @bw600 {
    gap: 20px;
    flex-wrap: wrap;
    flex-direction: column;
    align-items: center;
    grid-template-columns: 1fr;
    grid-template-areas:
      "nav"
      "subscribe"
      "vault";
  }

  &::after {
    content: "";
    position: absolute;
    top: 0;
    height: 2px;
    right: 0;
    width: calc(50% - 4%);
    background: linear-gradient(
      135deg,
      rgba(28, 27, 27, 1) 0%,
      rgba(255, 255, 255, 0) 70%
    );
  }

  &::before {
    content: "";
    position: absolute;
    top: 0;
    height: 2px;
    left: 0;
    width: calc(50% - 4%);
    background: linear-gradient(
      -135deg,
      rgba(28, 27, 27, 1) 0%,
      rgba(255, 255, 255, 0) 70%
    );
  }

  &__wrapper {
    grid-area: nav;
  }
  &__nav {
    display: flex;
    flex-direction: column;
    @media @bw960 {
      margin-bottom: 20px;
      padding-left: 20px;
    }
  }
  &__nav-link {
    position: relative;
    padding-left: 16px;
    margin-bottom: 14px;
    color: @black;
    text-decoration: none;
    font-weight: 600;
    font-size: 16px;
    @media @bw500 {
      font-weight: 600;
      font-size: 14px;
    }
    &:hover {
      color: @red;
    }
    &::before {
      content: "";
      position: absolute;
      left: 0;
      top: 0;
      bottom: 0;
      width: 4px;
      background-color: @red;
    }
  }

  &__subscribe-form {
    grid-area: subscribe;
  }

  &__vault {
    grid-area: vault;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 40px;
    padding-top: 20px;
    @media @bw960 {
      padding-left: 20px;
      padding-right: 20px;
      flex-direction: column;
      align-items: center;
    }
  }
  &__socials {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 20px;
    @media @bw960 {
      order: 1;
    }
  }
  &__terms {
    display: flex;
    gap: 30px;
    flex-direction: column;
    align-items: flex-start;
    gap: 12px;
    @media @bw960 {
      order: 2;
    }
  }

  &__riht,
  &__terms {
    @media @bw960 {
      margin-bottom: 10px;
      justify-content: center;
      width: 100%;
      text-align: center;
    }
  }

  &__copyrights {
    font-size: 16px;
    font-weight: 400;
    line-height: 22px;
    margin: 0;
    color: @black;
    @media @bw500 {
      margin-top: 20px;
      display: flex;
      align-self: end;
    }
  }

  &__terms-links {
    display: flex;
    gap: 60px;
    @media @bw960 {
      display: flex;
      gap: 10px;
      flex-direction: column;
      flex-wrap: nowrap;
      align-items: flex-start;
    }
  }

  &__terms-link {
    color: @black;
    text-decoration: none;
    font-size: 16px;
    font-weight: 600;
    line-height: 22px;
    transition: color 0.3s;
    // display: flex;
    gap: 20px;
    cursor: pointer;
  }

  &__Dignity {
    align-items: center;
    display: inline-flex;
    margin-right: 10px;
    gap: 8px;
    cursor: pointer;
    font-family: @font1;
    font-size: 16px;
    font-weight: 600;
    line-height: 22px;
    @media @bw960 {
      order: 2;
      align-self: flex-end;
    }
  }
  &__Dignity-icon {
    width: 100%;
    height: 100%;
    object-fit: contain;
    text-decoration: none;
    @media @bw370 {
      max-width: 65px;
      height: 65px;
    }
  }
  span.error {
    color: @red;
    display: block;
    margin: 5px 0 0;
  }

  .x-btn {
    display: flex;
    justify-content: center;
    align-items: center;
    outline: none;
    border: none;
    padding: 0;
    width: 60px;
    height: 60px;
    border-radius: 50%;
    background-color: @black;
    transition: background-color 0.2s;
  }
}
</style>
