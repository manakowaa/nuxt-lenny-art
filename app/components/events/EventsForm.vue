<template>
  <form class="events-form" @submit="onSubmit">
    <div class="events-form__list">
      <div class="events-form__group events-form__group--w50">
        <FieldRadio
          name="format"
          :options="[
            {
              label: 'Мастер-класс/семинар',
              value: 'seminar',
            },
            {
              label: 'Концерт/выступление',
              value: 'concert',
            },
            {
              label: 'Выставка/показ',
              value: 'show',
            },
            {
              label: 'Другое',
              value: 'other',
            },
          ]"
          :initialValue="'seminar'"
          :rules="{ required: true }"
          :submitCount="submitCount"
          :label="'Формат мероприятия:'"
          class="events-form__field"
        />
      </div>

      <div class="events-form__group events-form__group--w50">
        <FieldSelect
          name="amount"
          :options="[
            {
              label: 'до 20 человек',
              value: '20',
            },
            {
              label: 'от 20 до 100 человек',
              value: '100',
            },
            {
              label: 'от 100 до 500 человек',
              value: '500',
            },
            {
              label: 'более 500 человек',
              value: '1000',
            },
          ]"
          :initialValue="'20'"
          :rules="{ required: true }"
          :submitCount="submitCount"
          label="Планируемое количество посетителей:"
          placeholder="Выберите количество"
          class="events-form__field"
        />

        <FieldDate
          name="date"
          label="Дата проведения:"
          :rules="{ required: true }"
          :submitCount="submitCount"
        />
      </div>
    </div>

    <div class="events-form__section">
      <h6 class="events-form__section-title field-title">Контакные данные:</h6>

      <div class="events-form__list">
        <FieldInput
          name="first_name"
          label="Имя"
          placeholder="Имя"
          :rules="{ required: true }"
          :submitCount="submitCount"
          class="events-form__field events-form__field--w50"
        />

        <FieldInput
          name="last_name"
          label="Фамилия"
          placeholder="Фамилия"
          :rules="{ required: true }"
          :submitCount="submitCount"
          class="events-form__field events-form__field--w50"
        />

        <FieldInput
          name="phone"
          label="Телефон"
          placeholder="+7 (###) ###-##-##"
          :rules="{ required: true, phone: true }"
          mask="+7 (###) ###-##-##"
          :submitCount="submitCount"
          class="events-form__field events-form__field--w50"
        />

        <FieldInput
          name="email"
          label="Email"
          type="email"
          placeholder="Email"
          :rules="{ required: true, email: true }"
          :submitCount="submitCount"
          class="events-form__field events-form__field--w50"
        />
      </div>
    </div>

        <FieldText 
        name="text"
        label="Есть пожелания? Напишите нам:"
        :submitCount="submitCount"
        class="events-form__field"
        />

        <FieldCheck
          name="agreement"
          :rules="{ required: true }"
          :submitCount="submitCount"
          :label="`Я соглашаюсь с <a href='#' target='_blank'>пользовательским соглашением</a> и с <a href='#' target='_blank'>политикой</a> использования персональных данных`"
          class="events-form__field"
        />

    <div class="events-form__btns">
      <button type="submit" class="btn events-form__submit">Отправить</button>

      <button type="button" class="events-form__close-btn" @click="close">
        Закрыть
      </button>
    </div>
  </form>
</template>

<script setup>
import { useForm } from "vee-validate";

const emits = defineEmits(["close"]);

const { submitCount, handleSubmit } = useForm();

const close = () => {
  emits("close");
};

const onSubmit = handleSubmit((submitValues) => {
  console.log(submitValues);
  alert("Отправлено");

  close();
});
</script>

<style lang="less">
.events-form {
  &__list {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }
  &__field,
  &__group {
    width: 100%;
    &--w50 {
      width: calc(50% - 30px);

      @media @bw1020 {
        width: calc(50% - 15px);
      }
      @media @bw768 {
        width: 100%;
      }
    }
  }

  &__field {
    margin: 0 0 30px;
  }

  &__check {
    margin-bottom: 10px;
    &:last-child {
      margin-bottom: 0;
    }
  }

  &__section {
    margin: 0 0 20px;
  }

  &__section-title {
    margin: 0 0 10px;
  }

  &__btns {
    display: flex;
    align-items: center;
    margin-top: 10px;
    @media @bw768 {
      flex-direction: column;
      align-items: center;
    }
  }

  &__submit {
    width: calc(50% - 30px);

    @media @bw1020 {
      width: calc(50% - 15px);
    }
    @media @bw768 {
      width: 100%;
    }
  }

  &__close-btn {
    margin: 0 auto;
    padding: 4px 0;
    border: none;
    background: transparent;
    color: @black;
    font-weight: 600;
    font-size: 16px;
    line-height: 22px;
    text-decoration: underline;
    transition: color 0.2s;
    @media @bw768 {
      margin: 30px auto 0;
    }
    &:active {
      color: @red;
    }
    &:hover {
      @media (hover: hover) {
        color: @red;
      }
    }
  }
}
</style>
