<template>
  <div class="field">
    <label class="field__input-label">
      <span v-if="label" class="field__title field-title">
        {{ label }} 
      </span>

      <textarea
        class="field__textarea"
        :placeholder="placeholder"
        v-model="value"
      ></textarea>
    

    <span v-if="errorMessage && submitCount" class="field__error field-error">
      {{ errorMessage }}
    </span>
    </label>
  </div>
</template>

<script setup>
  import { useField } from "vee-validate";

  const props = defineProps({
    initialValue: {
      default: undefined,
    },
    name: {
      type: String,
      required: true,
    },
    label: {
      type: String,
      default: "",
    },
    placeholder: {
      type: String,
      default: "",
    },
    rules: {
      type: Object,
      default: () => ({}),
    },
    submitCount: {
      type: Number,
      default: 0,
    },
  });

  const { errorMessage, value } = useField(props.name, props.rules, {
    initialValue: props.initialValue,
  });
</script>