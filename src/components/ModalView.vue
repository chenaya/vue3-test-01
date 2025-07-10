<template>
  <div v-if="show" class="modal-overlay" @click.self="close">
    <div class="modal-content">
      <div class="modal-title">
        <h4>排行榜</h4>
        <button class="btn" @click="close">×</button>
      </div>
      <slot />
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalView",
  props: {
    show: {
      type: Boolean,
      required: true,
    },
  },
  emits: ["close"],
  methods: {
    close() {
      this.$emit("close");
    },
  },
};
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.btn {
  display: flex;
  /* justify-content: space-between; */
  position: absolute;
  right: 10px;
  top: 10px;
  /* align-items: center; */
  background: transparent;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
}

.modal-content {
  position: relative;
  background: #fff;
  padding: 1.5rem;
  border-radius: 10px;
  max-width: 500px;
  width: 90%;
}
</style>
