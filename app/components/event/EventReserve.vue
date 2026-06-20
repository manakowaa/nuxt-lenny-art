<template>
  <form class="event-reserve" @submit="onSubmit">
    <div class="event-reserve__checks">
      <h4
        class="event-reserve__section-title event-reserve__section-title--mb30"
      >
        Забронировать столик
      </h4>

      <FieldCheck
        v-for="(val, key) in checks"
        :key="key"
        :checkedValue="+key"
        name="table"
        :label="`${key} стол`"
        class="event-reserve__check"
        :submitCount="submitCount"
        :red="val.red || false"
        :disabled="val.disabled || false"
      />

      <span v-if="submitCount && !values.table?.length" class="field__error field-error">
    Это поле обязательно
  </span>

    </div>

    <div class="event-reserve__scheme">
      <div class="event-reserve__scheme-container">
        <h4 class="event-reserve__scheme-title">Сцена</h4>

        <div class="event-reserve__scheme-wrapper">
          <EventScene
            :checks="checks"
            :values="values"
            class="event-reserve__scene"
            @tableClick="onTableClick"
          />
        </div>
      </div>
    </div>

    <div class="event-reserve__order">
      <h4 class="event-reserve__section-title">Ваши пригласительные билеты</h4>

      <div
        class="event-reserve__tickets-list"
        data-caption="шт."
        data-currency="₽"
      >
        <div class="event-reserve__tickets">
          <div
            class="event-reserve__qty"
            data-caption="шт."
            :data-price="price.red"
          >
            {{ red }}
          </div>
          <div class="event-reserve__sum" data-currency="₽">
            {{ redCost }}
          </div>
        </div>

        <div class="event-reserve__tickets">
          <div
            class="event-reserve__qty"
            data-caption="шт."
            :data-price="price.black"
          >
            {{ black }}
          </div>
          <div class="event-reserve__sum" data-currency="₽">
            {{ blackCost }}
          </div>
        </div>
      </div>

      <div class="event-reserve__total" data-caption="Сумма" data-currency="₽">
        {{ redCost + blackCost }}
      </div>

      <button type="submit" class="btn btn--red event-reserve__submit">
        Купить билеты
      </button>
    </div>

    <div class="event-reserve__legend">
      <div class="event-reserve__price">
        <h4 class="event-reserve__section-title">
          Стоимость пригласительного билета
        </h4>

        <div
          class="event-reserve__price-list"
          id="reservePriceList"
          data-caption="₽ | 1 персона"
        >
          <div
            class="event-reserve__price-item event-reserve__price-item--red"
            data-caption="₽ | 1 персона"
          >
            {{ price.red }}
          </div>

          <div class="event-reserve__price-item" data-caption="₽ | 1 персона">
            {{ price.black }}
          </div>
        </div>
      </div>

      <div class="event-reserve__notation">
        <h4 class="event-reserve__section-title">Примечание</h4>

        <div class="event-reserve__note event-reserve__note--free">
          доступные места
        </div>
        <div class="event-reserve__note event-reserve__note--booked">
          забронировано
        </div>
      </div>
    </div>
  </form>
</template>

<script setup>
import { useForm } from "vee-validate";

const checks = ref({
  1: { red: true },
  2: {},
  3: {},
  4: { red: true },
  5: { disabled: true },
  6: {},
  7: { red: true },
  8: {},
  9: {},
  10: {},
  11: {},
});

const price = ref({ red: 1400, black: 1250 });

const { submitCount, handleSubmit, setFieldValue, values } = useForm({
  initialValues: {
    table: [],
  },
});

const black = computed(() => {
  return Array.isArray(values.table)
    ? values.table.reduce(function (sum, current) {
        return sum + (checks.value[current]?.red ? 0 : 1);
      }, 0)
    : 0;
});

const blackCost = computed(() => black.value * price.value.black);

const red = computed(() => {
  return Array.isArray(values.table)
    ? values.table.reduce(function (sum, current) {
        return sum + (checks.value[current]?.red ? 1 : 0);
      }, 0)
    : 0;
});

const redCost = computed(() => red.value * price.value.red);

const onSubmit = handleSubmit((submitValues) => {
  console.log(submitValues);
});

const onTableClick = (table) => {
    if (checks.value[table]?.disabled) return;

    const currentArray = Array.isArray(values.table) ? values.table : [];

    let newArray;

    if (currentArray.includes(table)) {
        newArray = currentArray.filter((check) => check !== table)
    } else {
        newArray = [...currentArray, table]
    }

    setFieldValue("table", newArray);
}
</script>

<style lang="less">
.event-reserve {
  display: grid;
  grid-template-columns: 405px calc(89% - 405px);
  grid-template-areas:
    "checks scheme"
    "order legend";
  width: 100%;
  @media @bw1660 {
    gap: 65px 6.5%;
    grid-template-columns: 400px calc(93.5% - 400px);
  }
  @media @bw1340 {
    grid-template-columns: 340px calc(93.5% - 340px);
  }
  @media @bw1020 {
    gap: 60px;
    grid-template-columns: auto 390px;
    grid-template-areas:
      "scheme scheme"
      "checks legend"
      "checks order";
  }
  @media @bw768 {
    grid-template-columns: 100%;
    grid-template-areas:
      "scheme"
      "legend"
      "checks"
      "order";
  }
  &__checks {
    grid-area: checks;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }

  &__order {
    grid-area: order;
  }
  &__scheme {
    grid-area: scheme;
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    @media @bw1020 {
      align-items: center;
    }
  }
  &__scheme-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    max-width: 780px;
  }

  &__legend {
    grid-area: legend;
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    text-align: right;
    @media @bw768 {
      align-items: flex-start;
      text-align: left;
    }
  }
  &__section-title {
    margin: 80px 0 20px;
    font-weight: 600;
    font-size: 18px;
    line-height: 25px;
    @media @bw500 {
      font-size: 16px;
      line-height: 22px;
    }
    &--mb30 {
      margin-bottom: 30px;
      @media @bw500 {
        margin-bottom: 20px;
      }
    }
  }

  &__check {
    margin-bottom: 10px;
    &:last-child {
      margin-bottom: 0;
    }
  }

  &__scheme-title {
    margin: 80px 0 40px;
    padding: 6px 56px;
    background-color: @black;
    color: @white;
    font-weight: 600;
    font-size: 16px;
    line-height: 22px;
  }
  &__scheme-wrapper {
    position: relative;
    width: 100%;
    &::after {
      content: "";
      display: block;
      width: 100%;
      padding-top: 51.15384%;
    }
  }

  &__scene {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }

  &__tickets-list {
    margin: 0 0 25px;
  }

  &__tickets {
    display: flex;
    justify-content: space-between;
    align-items: baseline;
    margin: 0 0 18px;
    @media @bw500 {
      margin-bottom: 13px;
    }
    &:last-child {
      margin-bottom: 0;
    }
  }

  &__qty {
    font-size: 16px;
    line-height: 22px;
    @media @bw500 {
      font-size: 14px;
      line-height: 19px;
    }
    &::after {
      content: " " attr(data-caption) " | " attr(data-price) " ";
    }
  }

  &__sum {
    font-weight: 600;
    margin-bottom: 18px;
    line-height: 25px;
    @media @bw500 {
      font-size: 16px;
      line-height: 22px;
    }
    &::after {
      content: attr(data-currency);
      margin-left: 4px;
      font-size: 0.95em;
    }
  }

  &__total {
    margin: auto;
    display: flex;
    justify-content: center;
    font-weight: 700;
    margin: 0 0 53px;
    &::before {
      content: attr(data-caption);
      margin-right: 30px;
    }
    &::after {
      font-size: 0.95em;
      margin-left: 4px;
      content: attr(data-currency);
    }
  }

  &__submit {
    width: 100%;
  }

  &__price {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    margin: 0 0 35px;
    @media @bw768 {
      align-items: flex-start;
      margin: 0 0 30px;
    }
  }

  &__price-item {
    position: relative;
    min-height: 24px;
    margin-bottom: 15px;
    padding-top: 2px;
    padding-left: 34px;
    font-size: 14px;
    line-height: 19px;
    &::before {
      content: "";
      display: block;
      position: absolute;
      top: 0;
      left: 0;
      width: 24px;
      height: 24px;
      background-color: @black;
    }
    &::after {
      content: attr(data-caption);
    }
    &--red {
      &::before {
        background-color: @red;
      }
    }
    &:last-child {
      margin-bottom: 0;
    }
  }

  &__notation {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    @media @bw768 {
      align-items: flex-start;
    }
  }

  &__note {
    position: relative;
    min-height: 24px;
    margin-bottom: 13px;
    padding-left: 54px;
    padding-top: 2px;
    font-size: 14px;
    line-height: 19px;
    @media @bw768 {
      padding-left: 45px;
    }
    &--free {
      &::before,
      &::after {
        content: "";
        box-sizing: border-box;
        display: block;
        position: absolute;
        top: 0;
        left: 0;
        width: 24px;
        height: 24px;
        border: 1px solid @black;
        border-radius: 50%;
      }
      &::after {
        left: 12px;
        border-color: @red;
      }
    }

    &--booked {
      &::before {
        content: "";
        display: block;
        position: absolute;
        top: 0;
        left: 0;
        width: 24px;
        height: 24px;
        border-radius: 50%;
        background-color: @gray_dark;
      }
    }
    &:last-child {
      margin-bottom: 0;
    }
  }
}
</style>
