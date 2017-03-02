<template>
  <div id="app">
    <img src="./assets/logo.png">
    <action-button text="Generate a new number" @click="generateNumber"></action-button>
    <template v-if="hasNumbers">
      <h2>Last 5 generated numbers</h2>
      <ul>
        <li v-for="number in lastFiveNumbers">{{ number }}</li>
      </ul>
      <h2>Smallest</h2>
      <p>{{ min || '-' }}</p>
      <h2>Largest</h2>
      <p>{{ max || '-' }}</p>
      <h2>Range</h2>
      <p>{{ range || '-' }}</p>
    </template>
  </div>
</template>

<script>
import ActionButton from './ActionButton.vue';


const rng = max => Math.ceil(Math.random() * max);


export default {
  components: {
    ActionButton
  },
  data() {
    return {
      numbers: []
    };
  },
  methods: {
    generateNumber() {
      /* This is the only place where data is mutated */
      this.numbers.push(rng(500));
    }
  },
  computed: {
    hasNumbers() {
      return this.numbers.length > 0;
    },
    lastFiveNumbers() {
      return this.numbers.slice(Math.max(this.numbers.length - 5, 0));
    },
    min() {
      return Math.min(...this.numbers);
    },
    max() {
      return Math.max(...this.numbers);
    },
    range() {
      return `${this.min} - ${this.max}`;
    }
  }
};

</script>

<style lang="scss">
@import "./assets/style";
@import "./assets/constants";

#app {
  font-family: Helvetica, Arial, sans-serif;
  text-align: center;
  color: $color-brand-secondary;
  margin-top: 60px;
}

a {
  color: $color-brand-primary;
}
</style>
