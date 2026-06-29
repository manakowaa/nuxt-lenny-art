<template>
  <section class="app-about">
    <div class="app-about__wrapper">
      <h2 class="app-about__title section-title">О НАС</h2>

      <div class="app-about__item">
        <h4 class="app-about__sub-title">Проект «Millennials»</h4>
        <p class="app-about__text app-about__text--1">
          Вдохновлен молодыми идейными людьми, увлеченными творчеством, эмоциями
          и желанием сделать мир лучше, проявить себя. У них есть талант и
          стремление, у нас возможность помочь им воплотить их мечту в
          реальность.
        </p>

        <img
          src="@/assets/images/about/pic.jpg"
          alt="pic"
          class="app-about__image"
        />
      </div>


    <div class="app-about__item-2">
      <div class="app-about__content-2">
        <h4 class="app-about__sub-title">
          Мы предоставляем площади для вашего мероприятия
        </h4>

        <p class="app-about__text app-about__text--2">
          И оказываем помощь с организацией, если вам это нужно. Наша цель:
          вовлечь в культурную жизнь города как можно больше людей, помочь
          молодым ребятам сделать первые шаги к своей мечте и рассказать всем о
          том, что их волнует.
        </p>
      </div>

      <img
        src="@/assets/images/about/pic2.jpg"
        class="app-about__image-2"
        alt="pic2"
      />
    </div>

    <div class="app-about__item-3">
      <div class="app-about__image-3-wrap">
        <img
          src="@/assets/images/about/pic3.jpg"
          class="app-about__image-3"
          alt="pic3"
        />
      </div>

      <div class="app-about__content-3">
        <p class="app-about__text app-about__text--3">
          Мы уже успешно организовали и провели более 100 проектов. Посмотрите,
          как это было классно.
        </p>

        <div class="app-about__link-wrap">
          <a href="#" class="app-about__link link">
            <span class="app-about__text"> Смотреть </span>
            <span class="link__arrow arrow">
              <SvgIcon
                name="arrow"
                class="arrow__icon"
                width="91"
                height="60"
              />
            </span>
          </a>
           </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>

</script>

<style lang="less">
.app-about {
  .container;
  &__sub-title {
    margin: 0 0 50px;
    width: 65.217%;
    font-weight: 700;
    font-size: 44px;
    line-height: 1.36;
    @media @bw1660 {
      width: 65.714%;
    }
    @media @bw1340 {
      max-width: 570px;
      font-size: 36px;
    }
    @media @bw1020 {
      max-width: 410px;
      width: 100%;
      font-size: 26px;
    }
    @media @bw500 {
      margin: 0 0 30px;
      font-size: 18px;
    }
  }
  &__text {
    box-sizing: border-box;
    width: 64.9925%;
    max-width: 100%;
    margin: 0 0 100px auto;
    font-size: 18px;
    line-height: 25px;
    @media @bw1020 {
      font-size: 16px;
      line-height: 22px;
    }
    @media @bw500 {
      font-size: 14px;
      line-height: 19px;
    }
  &--1,
  &--2 {
    @media @bw1020 {
      width: 100%;
      padding-left: 70px;
    }
    @media @bw768 {
      padding-left: 40px;
    }
    @media @bw768 {
      padding-left: 0;
    }
  }

  &--1 {
    @media @bw1020 {
      margin: 0 0 80px;
    }
    @media @bw768 {
      margin-bottom: 60px;
    }
  }
  &--2 {
    @media @bw1020 {
      margin: 0;
    }
    @media @bw768 {
      margin-bottom: 50px;
    }
  }
  &--3 {
    width: 100%;
    margin: 0 0 100px;
    @media @bw1020 {
      margin: 0;
      max-width: 280px;
    }
    @media @bw768 {
      margin-bottom: 30px;
    }
  }
}

  &__image {
    display: block;
    width: 65.217%;
    @media @bw1660 {
      width: 65.714%;
    }
    @media @bw1020 {
      width: 100%;
    }
  }
  &__item {
    margin-bottom: 100px;
    @media @bw1020 {
      margin-bottom: 50px;
    }
    @media @bw768 {
      margin-bottom: 60px;
    }
  }
  &__item-2 {
    position: relative;
    @media @bw1020 {
      display: flex;
      align-items: center;
      margin-bottom: 50px;
    }
    @media @bw768 {
      flex-direction: column;
      align-items: stretch;
    }
  }

  &__image-2 {
    display: block;
    position: absolute;
    right: 0;
    bottom: 100%;
    margin-bottom: -105px;
    width: calc(34.783% - 60px);
    @media @bw1660 {
      width: calc(34.286% - 40px);
    }
    @media @bw1340 {
      width: calc(34.286% - 30px);
    }
    @media @bw1020 {
      flex-shrink: 0;
      position: static;
      bottom: auto;
      margin-left: 30px;
      width: 37%;
      margin-bottom: 0;
    }
    @media @bw768 {
      align-self: flex-end;
      width: 68.928%;
      max-width: 404px;
    }
  }
  &__item-3 {
    display: flex;
    align-items: flex-end;
    @media @bw1020 {
      flex-direction: column;
      align-items: stretch;
    }
  }
  &__image-3-wrap {
    box-sizing: border-box;
    flex-shrink: 0;
    position: relative;
    width: calc(65.217% + 60px);
    padding: 18px 8px 0 38px;
    @media @bw1660 {
      width: calc(65.714 + 40px);
    }
    @media @bw1340 {
      width: calc(65.714 + 30px);
    }
    @media @bw1020 {
      width: 100%;
      margin: 0 0 80px;
    }
    @media @bw500 {
      margin-bottom: 60px;
    }
    &::before {
      content: "";
      display: block;
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      height: 67.54%;
      background-color: @red;
    }
  }
  &__image-3 {
    display: block;
    position: relative;
    width: 100%;
    z-index: 1;
  }
  &__content-3 {
    box-sizing: border-box;
    flex-grow: 1;
    margin-left: 60px;
    @media @bw1660 {
      margin-left: 40px;
    }
    @media @bw1340 {
      margin-left: 30px;
    }
    @media @bw1020 {
      display: flex;
      align-items: flex-end;
      justify-content: space-between;
      width: 100%;
      max-width: 100%;
      margin-left: 0;
    }
    @media @bw768 {
      flex-direction: column;
      align-items: flex-start;
    }
  }
  &__link-wrap {
    display: flex;
    align-items: center;
    width: 100%;
    height: 60px;
    @media @bw1020 {
      width: 260px;
    }
    @media @bw768 {
      width: 280px;
      margin-left: auto;
      max-width: 100%;
    }
  }
  &__link {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    height: 0;
  }
}
</style>
