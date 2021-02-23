<template>
  <h1>{{ title }}</h1>
  <p>Pardon the css</p>
  <div class="tableContainer">
    <PoolTable />
    <PoolTable />
    <PoolTable />
    <PoolTable />
    <PoolTable />
    <PoolTable />
  </div>
</template>

<script>
import PoolTable from "./components/PoolTable";

export default {
  components: {
    PoolTable,
  },
  data() {
    return {
      title: "Playing around with Vue",
    };
  },
  methods: {},
};
</script>

<style>
#app,
.modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  min-height: 100vh;
}
.tableContainer {
  display: flex;
  flex-direction: row;
  justify-content: center;
}
</style>
