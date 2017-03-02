<template>
  <button @click="onClick">{{ text }}</button>
</template>

<script>

export default {
  props: {
    text: {
      type: String,
      required: true
    }
  },
  methods: {
    onClick() {
      this.$emit('click');
    }
  }
};

</script>

<style lang="scss" scoped>
@import "./assets/constants";

:local {
  display: block;
  margin: 20px auto;
  padding: 10px 20px;

  font-size: $font-size-small;

  color: white;

  border: none;
  background: $color-brand-secondary;

  &:hover {
    border-color: $color-brand-primary;
  }

  &:focus {
    outline: none;
  }

  &:active {
    color: white;
    background-color: $color-brand-primary;
  }
}
</style>
