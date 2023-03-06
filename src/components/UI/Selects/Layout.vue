<template>
  <div class="select-wrap">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'layout',
};
</script>

<style scoped>
.select-wrap >>> .primary-select {
  position: relative;
  outline: none;
  height: 100%;
  line-height: 250%;
}

.select-wrap >>> .primary-select .selected {
  height: 100%;
  background-color: transparent;
  border-radius: .6rem;
  border: 1px solid var(--border-color);
  padding-left: .6em;
  cursor: pointer;
  user-select: none;
  display: flex;
  align-items: center;
}

.select-wrap >>> .primary-select .selected.open {
  border: 1px solid var(--border-color);
  border-radius: .6rem .6rem 0px 0px;
}

.select-wrap >>> .primary-select .selected:after {
  position: absolute;
  content: "";
  top: 50%;
  right: 1em;
  width: 0;
  height: 0;
  border: 5px solid transparent;
  border-color: var(--text-color) transparent transparent transparent;
}

.select-wrap >>> .primary-select .items {
  color: var(--text-color);
  border-radius: 0px 0px .6rem .6rem;
  overflow: hidden;
  border-right: 1px solid var(--border-color);
  border-left: 1px solid var(--border-color);
  border-bottom: 1px solid var(--border-color);
  position: absolute;
  background-color: var(--main-bg-color);
  left: 0;
  right: 0;
  z-index: 1;
}

.select-wrap >>> .primary-select .items div {
  color: var(--text-color);
  padding-left: 1em;
  cursor: pointer;
  user-select: none;
}

.select-wrap >>> .primary-select .items div:hover {
  background-color: var(--primary-color);
}

.select-wrap >>> .selectHide {
  display: none;
}
</style>