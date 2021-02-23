<template>
  <teleport to=".modals" v-if="showModal">
    <Modal :header="header" :text="text" theme="sale" @close="toggleModal" />
  </teleport>
  <div class="poolTable">
    <div class="poolTable_container" :class="{ paused: tablePaused === true }">
      <Timer />
      <Tab @open="toggleModal" />
    </div>
  </div>
</template>

<script>
import Timer from "./Timer";
import Tab from "./Tab";
import Modal from "./Modal";

export default {
  components: {
    Timer,
    Tab,
    Modal,
  },
  data() {
    return {
    tablePaused: false,
      showModal: false,
      header: "This is a modal test",
      text: "Random text to fill the void",
    };
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
    togglePaused(){
        this.tablePaused = !this.tablePaused;
    }
  },
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
.poolTable_container.paused{
    background-color: red;
}
</style>
