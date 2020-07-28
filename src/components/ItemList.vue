<template>
  <div>
    <div>ItemList</div>
    <div v-for="item in items" :key="item.name">
      <div class="item" :class="{ over500: item.price >= 500 }">
        <div class="name">名前: {{ item.name }}</div>
        <div class="price">{{ item.price }} 円</div>
        <div v-if="item.price >= 10000">高額商品</div>
      </div>
    </div>
    <div>
      <label>
        名前
        <input type="text" v-model="newItemName" />
      </label>
      <label>
        値段
        <input type="text" v-model="newItemPrice" />
      </label>
      <button @click="addItem">add</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ItemList",
  data() {
    return {
      items: [
        { name: "リンゴ", price: 100 },
        { name: "卵", price: 150 }
      ],
      newItemName: "",
      newItemPrice: ""
    };
  },
  methods: {
    addItem() {
      if (this.newItemName != "" && this.newItemPrice != "") {
        this.items.push({ name: this.newItemName, price: this.newItemPrice });
        this.newItemName = "";
        this.newItemPrice = "";
      }
    }
  }
};
</script>

<style>
.over500 {
  color: red;
}
</style>
