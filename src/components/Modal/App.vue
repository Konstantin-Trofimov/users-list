<template>
  <layout
    @modal-shown="$emit('modal-shown')"
    title="Добавление пользователя"
  >
    <Form
      :users="users"
      @update:users="handleAddNewUser" 
    />
  </layout>
</template>

<script>
import Layout from './Layout.vue';
import Form from './Form';


export default {
  name: 'modal',

  components: {
    Form,
    Layout,
  },

  props: {
    users: {
      type: Array,
      required: true,
      default: () => [],
    },
  },

  methods: {
    handleAddNewUser(newUser) {
      this.$emit('update:users', newUser);
    },
  },
};
</script>