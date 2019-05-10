<template>
  <div>
    <h2>ItemList</h2>
    <div v-for="item in items" :key="item.name">
      <div class="item" :class="{over500: item.price >= 500}">
        <div class="name">名前: {{ item.name }}</div>
        <div class="price">{{ item.price }} 円</div>
        <div v-if="item.price >= 10000">高額商品</div>
      </div>
    </div>
    <p>
      <label for>
        名前
        <input type="text" v-model="newItemName">
      </label>
      <label for>
        価格
        <input type="text" v-model="newItemPrice">
      </label>
      <button @click="addItem">追加</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "ItemList",
  data() {
    return {
      items: [
        { name: "たまご", price: 100 },
        { name: "りんご", price: 160 },
        { name: "なろう講習会参加費", price: 500 }
      ]
    };
  },
  methods: {
    addItem: function() {
      if (
        this.newItemName === "" ||
        this.newItemPrice === "" ||
        this.newItemName === undefined ||
        this.newItemPrice === undefined
      ) {
        return;
      }
      this.items.push({ name: this.newItemName, price: this.newItemPrice });
      this.newItemName = "";
      this.newItemPrice = "";
    }
  }
};
</script>

<style>
.over500 {
  color: red;
}
</style>