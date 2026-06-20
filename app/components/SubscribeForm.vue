<template>
  <form class="subscribe-form" novalidate @submit.prevent="onSubmit">
    <h4 class="subscribe-form__title">
      Подпишись и будь в курсе происходящего
    </h4>

    <div class="subscribe-form__wrapper">
      <div class="subscribe-form__field-wrapper">
        <input
          v-model="email"
          type="email"
          placeholder="Email"
          class="subscribe-form__input"
        />

        <span
          v-if="submitCount && (!email || !emailIsValid)"
          class="subscribe-form__error field-error"
        >
          {{
            email && !emailIsValid
              ? "Email указан неверно"
              : "Это поле обязательно"
          }}
        </span>
      </div>

      <button type="submit" class="subscribe-form__submit">Подписаться</button>
    </div>

    <label class="subscribe-form__check check">
      <input
        v-model="agreement"
        :true-value="1"
        :false-value="0"
        type="checkbox"
        class="check__input"
      />
      <span class="check__mark"></span>
      <span class="check__caption check__caption--s">
        Согласен на обработку персональных данных
      </span>
    </label>

    <span
      v-if="submitCount && !agreement"
      class="subscribe-form__error field-error"
    >
      Это поле обязательно
    </span>
  </form>
</template>

<script setup>
const email = ref("");
const agreement = ref(0);

const submitCount = ref(0);

const emailIsValid = computed(() => {
  return /^[-\w.]+@([A-z0-9][-A-z0-9]+\.)+[A-z]{2,6}$/.test(email.value);
});

const onSubmit = () => {
  submitCount.value += 1;
  if (!email.value || !emailIsValid.value || !agreement.value) return;

  console.log({ email: email.value, agreement: agreement.value });
  alert("Подписка оформлена");
};
</script>

<style lang="less">
.subscribe-form {
  width: 405px;
  max-width: 100%;

  &__title {
    margin: 0 0 25px;
    font-size: 16px;
    line-height: 22px;
    @media @bw500 {
      margin: 0 0 15px;
      font-weight: 400;
      font-size: 13px;
      line-height: 18px;
    }
  }
  &__wrapper {
    display: flex;
    align-items: flex-start;
    @media @bw500 {
      margin: 0 -20px;
    }
  }
  &__field-wrapper {
    flex-grow: 1;
    display: flex;
    flex-direction: column;
  }

  &__input {
    box-sizing: border-box;
    width: 100%;
    height: 49px;
    padding: 0 25px;
    border: none;
    background-color: @white;
    font-size: 14px;
    line-height: 19px;
    @media @bw500 {
      height: 46px;
      padding: 0 20px;
      font-size: 12px;
      line-height: 16px;
    }
  }

  &__submit {
    flex-shrink: 0;
    box-sizing: border-box;
    height: 49px;
    padding: 5px 25px;
    border: none;
    background-color: @black;
    color: @white;
    font-size: 14px;
    line-height: 19px;
    @media @bw500 {
      height: 46px;
      padding: 5px 20px;
      font-size: 12px;
      line-height: 16px;
    }
    &:hover,
    &:active {
      background-color: @red_dark;
      color: @white;
    }
  }
  &__check {
    margin-top: 15px;
  }

  &__error {
    margin: 5px 0 0;
  }
}
</style>
