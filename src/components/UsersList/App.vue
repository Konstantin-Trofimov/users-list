<template>
  <layout>
    <primary-button 
      @click.native="$emit('modal-shown', true)"
    >
    Добавить
    </primary-button>

    <List 
      :users="users" 
      class="list"
    />
  </layout>
</template>

<script>
import Layout from './Layout.vue';
import List from './List.vue';
import PrimaryButton from '../UI/Buttons/PrimaryButton';

export default {
  name: 'users-list',

  components: {
    List,
    Layout,
    PrimaryButton,
  },

  props: {
    users: {
      type: Array,
      required: true,
      default: () => [],
    },
  },
};
</script>