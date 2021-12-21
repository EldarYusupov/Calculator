<template>
  <label class="base-select">
    <p v-if="label">{{ label }}</p>

    <select :disabled="disabled" v-model="value">
      <option v-for="(option, index) in options" :key="index">{{ option }}</option>
    </select>
  </label>
</template>

<script>
export default {
  name: "BaseSelect",
  props: {
    options: Array,
    label: String,
    disabled: Boolean
  },
  data() {
    return {
      value: null
    }
  },

  watch: {
    value(v) {
      this.$emit('input', v)
    }
  }
}
</script>

<style>
.base-select {
  flex: 1;
}

select {
  width: 100%;
}
</style>
