<template>
  <div class="Tab">
    <div class="items">{{ tab.length }}</div>
    <button @click="pay">Pay</button>
    <button @click="addToTab">Tab</button>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  data() {
    const tab = ref([]);

    function pay() {
      console.log("Do something");
    }
    function addToTab() {
      tab.value.push(1);
    }
    return {
      tab,
      pay,
      addToTab,
    };
  },
};
</script>

<style scoped>
.items {
  color: white;
  position: relative;
  top: 130px;
  left: 60px;
}
</style>
