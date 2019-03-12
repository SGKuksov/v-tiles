<template>
  <div class="bar">
    <div class="row" v-if="printItems.length">
      <item v-for="(item, i) in printItems" :key="i" :type="item" />
    </div>
    <div class="row">
      <button @click="addItemTypeOne">
        Type one + 1
      </button>
      <button @click="addItemTypeTwo">
        Type two + 1
      </button>
    </div>
  </div>
</template>

<script>
import Item from "./Item.vue";

export default {
  components: {
    Item
  },
  data() {
    return {
      redItems: [],
      greenItems: []
    };
  },
  methods: {
    addItemTypeOne() {
      this.redItems.push({
        type: "one"
      });
    },
    addItemTypeTwo() {
      this.greenItems.push({
        type: "two"
      });
    }
  },
  computed: {
    printItems() {
      let items = [];
      let separator = [];
      let maxLength = 10;

      if (this.redItems.length && this.greenItems.length) {
        separator = [{type: 'separator'}];
      }

      let deltaRed = 0;
      let deltaBlue = 0;
      const sumLength = this.redItems.length + this.greenItems.length

      if (sumLength <= 10) {
        console.log('Ok!');
      } else if (sumLength > 10) {
        alert(1)

        if (this.redItems.length > 5) {
          deltaRed = this.redItems.length
        }
      }

      items = [...this.redItems, ...separator, ...this.greenItems];

      return items;
    }
  }
};
</script>

<style lang="scss">
.row {
  display: flex;
  width: 100%;
  align-items: center;
  justify-content: center;
}
</style>
