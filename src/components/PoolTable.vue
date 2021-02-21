<template>
  <div class="poolTable">
    <div class="poolTable_container">
      <Timer />
      <Tab />
    </div>
  </div>
</template>

<script>
import Timer from "./Timer";
import Tab from "./Tab";

export default {
  setup() {
    return {
      Timer,
      Tab,
    };
  },
  methods: {},
};
</script>

<style scoped>
.poolTable {
  width: 200px;
  height: 300px;
  background-color: saddlebrown;
  display: flex;
  margin: 20px;
  transition: all 0.25s ease;
  border-radius: 15px;
}
.poolTable:hover {
  transform: scale(1.1, 1.1);
}
.poolTable_container {
  width: 160px;
  height: 260px;
  background-color: green;
  margin: 20px;
}
</style>
