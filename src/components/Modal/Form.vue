<template>
  <form 
    @submit.prevent="handleAddNewUser" 
    class="form"
  >
    <primary-input
      name="name"
      label="Имя" 
    />

    <primary-input
      name="phone"
      label="Телефон"
      type="number" 
    />

    <primary-select
      @input="handleGetSupervisorsId"
      :options="users"
      label="Начальник"
    />

    <primary-button
      btnExtraStyle="width-50"
      type="submit"
    >
    Сохранить
    </primary-button>
  </form>
</template>

<script>
import PrimaryButton from '../UI/Buttons/PrimaryButton.vue';
import PrimaryInput from '../UI/Inputs/PrimaryInput.vue';
import PrimarySelect from '../UI/Selects/PrimarySelect.vue';

export default {
  name: 'Form',

  components: {
    PrimaryButton,
    PrimaryInput,
    PrimarySelect,
  },

  props: {
    users: {
      type: Array,
    }
  },

  data() {
    return {
      supervisorId: null,
      name: null,
      phone: null,
    }
  },

  methods: {
    handleGetSupervisorsId(id) {
      this.supervisorId = id;
    },

    handleAddNewUser(evt) {
      const form = evt.target
      const { name, phone } = form.elements;

      const newUser = {
        id: String(Date.now()),
        name: name.value,
        phone: phone.value,
        childrens: [],
        supervisor: this.supervisorId,
      };

      if (name.value && phone.value) {
        this.$emit('update:users', newUser);

        form.reset()
      };
    },
  },
};
</script>