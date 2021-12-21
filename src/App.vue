<template>
  <div id="app">
    <div class="wrapper">
      <BaseInput type="number" v-model="args[0]" placeholder="Argument 1" label="Enter argument 1" />
      <BaseInput type="number" v-model="args[1]" placeholder="Argument 2" label="Enter argument 2" />
      <BaseSelect :disabled="!args[0] || !args[1]" :options="selectOptions" v-model="method" placeholder="Method" label="Select Method" />

      <p v-if="calcValue !== null">Result: {{ calcValue }}</p>
    </div>
  </div>
</template>

<script>
import BaseInput from "./components/BaseInput";
import BaseSelect from "./components/BaseSelect";
export default {
  name: 'App',
  components: {BaseSelect, BaseInput},
  data() {
    return {
      args: [null, null],
      method: null,
      selectOptions: ['-', '+', '*', '/']
    }
  },
  computed: {
    calcValue () {
      if (this.args[0] && this.args[1] && this.method) {
        let res = 0
        switch (this.method) {
          case '+':
            res = +this.args[0] + +this.args[1]
            break
          case '-':
            res = +this.args[0] - +this.args[1]
            break
          case '*':
            res = +this.args[0] * +this.args[1]
            break
          case '/':
            res = +this.args[0] / +this.args[1]
            break
        }

        return Math.round(res)
      } else return null
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.wrapper {
  display: flex;
  flex-direction: column;
  width: 300px;
  margin: 0 auto;
}
</style>
