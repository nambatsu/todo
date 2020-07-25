<template>
  <div>
    <div>ItemList</div>
    <div v-for="item in items" :key="item.name">
      <div class="item">
        <div class="name">名前: {{ item.name }}</div>
        <div class="price">{{ item.price }} 円</div>
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
      newItemPrice: 0
    };
  },
  methods: {
    addItem() {
      this.items.push({ name: this.newItemName, price: this.newItemPrice });
      this.newItemName = "";
      this.newItemPrice = 0;
    }
  }
};
</script>

<style></style>
