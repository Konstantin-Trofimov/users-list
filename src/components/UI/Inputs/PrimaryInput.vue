<template>
  <div class="form-control">
    <label>
      <span>{{ label }}</span>
    </label>
    
    <input
      :name="name" 
      :type="type"
      class="primary-input" 
      >
  </div>
</template>

<script>
export default {
  name: 'primary-input',

  props: {
    type: {
      type: String,
      default: 'text'
    },
    name: {
      type: String,
    },
    label: {
      type: String,
    },
  },
};
</script>

<style scoped>
.primary-input {
  border: 1px solid var(--border-color);
  border-radius: .3rem;
  padding: .3rem .4rem .4rem;
  outline: none;
}

.primary-input::-webkit-outer-spin-button,
.primary-input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
</style>