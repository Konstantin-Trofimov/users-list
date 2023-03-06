<template>
  <ul class="list">
    <li>
      <div>Имя</div>
      <div>Телефон</div>
    </li>
    
    <list-item 
      v-for="user in users"
      :key="user.id"
      :user="user"
    />
  </ul>
</template>

<script>
import ListItem from './ListItem.vue';

export default {
  name: 'list',

  components: {
    ListItem,
  },

  props: {
    users: {
      type: Array,
      required: true,
    },
  },
};
</script>