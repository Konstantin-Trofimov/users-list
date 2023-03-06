<template>
 <div class="list-wrap">
  <slot></slot>
 </div>
</template>

<script>
export default {
  name: 'layout',
};
</script>

<style scoped>
.list-wrap >>> ul {
  margin-left: 0; 
  padding-left: 0;
  min-width: 11rem;
}

.list-wrap >>> li {
  list-style-type: none;
  display: grid;
  grid-template-columns: auto 11rem;
}

.list-wrap >>> li div {
  display: flex;
  align-items: center;
  justify-content: start;
  padding: .5rem;
  border: 1px solid var(--border-color);
}
</style>