<template>
  <button
    :class="btnExtraStyle"
    class="primary-btn"
  >
    <span>
      <slot></slot>
    </span>
  </button>
</template>

<script>
export default {
  name: 'primary-button',

  props: {
    btnExtraStyle: {
      type: String,
    },
  },
};
</script>

<style scoped>
.primary-btn {
  height: 2rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: var(--primary-color);
  border: 1px solid var(--border-color);
  border-radius: .6rem;
  padding: .2rem 1rem;
  cursor: pointer;
}

.primary-btn.width-50 {
  width: 50%;
}
</style>