<template>
  <div id="app">
    <div class="main-wrap">
      <users-list 
        @modal-shown="handleShowModal" 
        :users="users" 
      />

      <modal
        v-show="isModalVisible"
        @modal-shown="handleShowModal" 
        :users="users"
        @update:users="handleAddNewUser"
      />
    </div>
  </div>
</template>

<script>
import UsersList from './components/UsersList/App.vue';
import Modal from './components/Modal/App.vue';
import json from './assets/json/users';

export default {
  name: 'App',

  components: {
    UsersList,
    Modal,
  },

  data() {
    return {
      users: json,
      isModalVisible: false,
    }
  },

  watch: {
    users(data) {
      this.saveData(data);
    },
  },

  methods: {
    handleShowModal(payload) {
      this.isModalVisible = payload;
    },

    handleAddNewUser(newUser) {
      this.users.push(newUser);

      this.users.map((user, i, users) => {
        if (user.id === newUser.supervisor) {
          user.childrens.push(parseInt(newUser.id)); 

          newUser.parents = this.setNewUserParents(user.parents); 

          this.users = this.deleteElementInArray(this.users, -1); 

          this.users = this.insertToArray(users, i, newUser); 
        }

        return user;
      });
    },

    setNewUserParents(parents) {
      return parents ? parseInt(parents) + 1 : 1;
    },
    
    deleteElementInArray(array, item = 0){
      return array.pop(array.at(item));
    },

    insertToArray(array, i, item) {
      return [
        ...array.slice(0, i + 1),
        item,
        ...array.slice(i + 1),
      ];
    },

    saveData(data) {
      localStorage.setItem('users', JSON.stringify(data));
    }
  },

  mounted() {
    if (localStorage.getItem('users')) {
      this.users = JSON.parse(localStorage.getItem('users'));
    } 

    this.saveData(this.users);
  },
};
</script>