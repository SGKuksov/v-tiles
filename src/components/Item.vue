<template>
  <div
    class="item"
    :class="{
      'item--typeOne': type.type === 'one',
      'item--typeTwo': type.type === 'two',
      'item--separator': type.type === 'separator'
    }"
  >
    {{ type.type }}
  </div>
</template>

<script>
export default {
  props: {
    type: {
      type: Object,
      default() {
        return {
          type: "separator"
        };
      }
    }
  }
};
</script>

<style lang="scss">
* {
  box-sizing: border-box;
}

.item {
  display: inline-block;
  height: 50px;
  width: 50px;

  &--typeOne {
    background-color: rgb(202, 64, 64);
  }
  &--typeTwo {
    background-color: rgb(81, 163, 33);
  }
  &--separator {
    background-color: #fff;
    border: 1px solid #000;
  }
}
</style>
