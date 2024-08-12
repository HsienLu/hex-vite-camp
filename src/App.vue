<script setup>
import {ref} from "vue";

const drinkData = ref([
  {
    Item: "珍珠奶茶",
    Description: "香濃奶茶搭配QQ珍珠",
    Price: 50,
    Stock: 20,
  },
  {
    Item: "冬瓜檸檬",
    Description: "清新冬瓜配上新鮮檸檬",
    Price: 45,
    Stock: 18,
  },
  {
    Item: "翡翠檸檬",
    Description: "綠茶與檸檬的完美結合",
    Price: 55,
    Stock: 34,
  },
  {
    Item: "四季春茶",
    Description: "香醇四季春茶，回甘無比",
    Price: 45,
    Stock: 10,
  },
  {
    Item: "阿薩姆奶茶",
    Description: "阿薩姆紅茶搭配香醇鮮奶",
    Price: 50,
    Stock: 25,
  },
  {
    Item: "檸檬冰茶",
    Description: "檸檬與冰茶的清新組合",
    Price: 45,
    Stock: 20,
  },
  {
    Item: "芒果綠茶",
    Description: "芒果與綠茶的獨特風味",
    Price: 55,
    Stock: 18,
  },
  {
    Item: "抹茶拿鐵",
    Description: "抹茶與鮮奶的絕配",
    Price: 60,
    Stock: 20,
  },
]);
const newItemName = ref("");
const reduceStack = (drink) => {
  if (drink.Stock == 0) {
    return;
  }
  drink.Stock--;
};
const addStack = (drink) => {
  drink.Stock++;
};
const changeItemName = (e) => {
  newItemName.value = e.target.value;
  console.log(newItemName.value);
};
const confirmName = (drink) => {
  if (newItemName.value == "") {
    return;
  }
  drink.Item = newItemName.value;
  newItemName.value = "";
};
</script>

<template>
  <div class="container">
    <table>
      <thead>
        <tr>
          <th>品項</th>
          <th>價格</th>
          <th>描述</th>
          <th>庫存</th>
          <th>操作庫存</th>
          <th>更改商品名稱</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(drink, i) in drinkData" :key="i">
          <td>{{ drink.Item }}</td>
          <td>{{ drink.Price }}</td>
          <td>{{ drink.Description }}</td>
          <td>{{ drink.Stock }}</td>
          <td>
            <button type="button" @click="reduceStack(drink)">-</button>
            <button type="button" @click="addStack(drink)">+</button>
          </td>
          <td>
            <input type="text" @change="changeItemName" />
            <button type="button" @click="confirmName(drink)">更改</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped></style>
