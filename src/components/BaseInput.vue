<template>
  <label class="base-input">
    <p v-if="label">{{ label }}</p>
    <input :placeholder="placeholder" :type="type" v-model="value" @input="emitValue">
  </label>
</template>

<script>
export default {
  name: "BaseInput",
  props: {
    placeholder: String,
    label: String,
    type: {
      type: String,
      default: 'text'
    }
  },
  data() {
    return {
      value: ''
    }
  },
  methods: {
    emitValue() {
      this.$emit('input', this.value)
    }
  }
}
</script>

<style>
input {
  width: 100%;
}
</style>
