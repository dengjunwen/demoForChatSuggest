<template>
  <div class="merchants">
    <h2>商户列表</h2>
    <ul>
      <li class="merchant-item" v-for="(merchant, index) in merchants" :key="index" @click="selectMerchant(merchant)">
        {{ merchant.name }}
      </li>
    </ul>
  </div>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  props: {
    merchants: {
      type: Array,
      required: true,
    },
    selectMerchant: {
      type: Function,
      required: true,
    },
  },
});
</script>

<style>
.merchants {
  flex: 2;
  margin-right: 1rem;
  background-color: #fff;
  padding: 1rem;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.merchant-item {
  display: flex;
  align-items: center;
  padding: 1rem;
  cursor: pointer;
  transition: background-color 0.2s ease;
  border-radius: 1px;
  border-bottom: 1px solid #e3e0e0;
}

.merchant-item:last-child {
  border-bottom: none;
}

.merchant-item:hover {
  background-color: #f5f5f5;
}

.merchant-item.active {
  background-color: #e8f0fe;
}

.merchant-avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  margin-right: 1rem;
  background-color: #e8e8e8;
}


</style>
