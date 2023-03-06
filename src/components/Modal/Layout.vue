<template>
  <div class="modal">
    <div 
      @click="$emit('modal-shown', false)" 
      v-html="closeSimbol"
      class="close"
    >
    </div>

    <span class="title">{{ title }}</span>

    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'layout',

  data() {
    return {
      closeSimbol: '&#x2716',
    }
  },

  props: {
    title: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
.modal {
  position: relative;
  width: 20rem;
  height: 14rem;
  padding: 1rem 1.4rem 1.4rem;
  border: 2px solid var(--border-color);
}

.close {
  position: absolute;
  top: .5rem;
  right: .5rem;
  cursor: pointer;
}

.form {
  margin-top: 1.6rem;
  min-height: 11rem;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.form >>> .form-control {
  display: grid;
  grid-template-columns: 100px 1fr;
  grid-template-rows: 30px;
}

.form >>> .form-control label {
  width: 100px;
  display: flex;
  align-items: center;
}

</style>