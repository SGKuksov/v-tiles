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
      let maxLength = 10; // базовая настройка
      let maxLeftLength;
      let maxRightLength;

      if (this.redItems.length && this.greenItems.length) {
        separator = [{ type: "separator" }];
      }

      const sumLength = this.redItems.length + this.greenItems.length;

      if (sumLength > maxLength) {
        // if (this.redItems.length === 5) {
        //   maxLeftLength = 5;
        // }
        // if (this.greenItems.length === 5) {
        //   maxRightLength = 5;
        // }

        if (this.redItems.length > 5) {
          maxRightLength = maxLength - this.redItems.length;

          // if (maxLength - this.redItems.length === 3) {
          //   maxRightLength = 3;
          // }
        }

        if (this.greenItems.length > 5) {
          maxLeftLength = maxLength - this.greenItems.length;

          // if (maxLength - this.greenItems.length === 3) {
          //   maxLeftLength = 3;
          // }
        }

        // if (this.greenItems.length <= 5) {
        //   // deltaRed = this.redItems.length;
        // }
        // if (this.greenItems.length > 5) {
        //   // deltaRed = this.redItems.length;
        // }

        // for (let i = 0; i < maxLeftLength; i += 1) {
        //   items.push(this.redItems[i]);
        // }
        // items.push(separator[0]);
        // for (let i = 0; i < maxRightLength; i += 1) {
        //   items.push(this.greenItems[i]);
        // }
        items = [...this.redItems, ...separator, ...this.greenItems];
      } else if (sumLength <= maxLength) {
        items = [...this.redItems, ...separator, ...this.greenItems];
      }

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
