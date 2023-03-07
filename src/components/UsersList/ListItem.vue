<template>
  <li 
    :style="{ marginLeft: this.user.supervisor ? `${this.user.parents * 30}px` : null }"
    class="item"  
  >
    <div>{{ userIsFolder }} {{  user.name }}</div>

    <div> {{ user.phone }}</div>
  </li>
</template>

<script>
export default {
  name: 'list-item',

  props: {
    user: {
      type: Object,
      required: true,
    },
  },

  computed: {
    userIsFolder() {
      return this.user.childrens.length > 0 ? '+' : null;
    },
  },
};
</script>