<template>
  <div class="Tab">
    <div class="items">{{ tab.length }}</div>
    <button @click="testEmit">Pay</button>
    <button @click="addToTab">Tab</button>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  methods: {
    testEmit() {
      this.$emit("open");
    },
  },
  data() {
    const tab = ref([]);

    function addToTab() {
      tab.value.push(1);
    }
    return {
      tab,
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
