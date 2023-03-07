<template>
  <div class="form-control">
    <label>
      <span>{{ label }}</span>
    </label>
    <layout>
      <div
        @blur="selectIsOpen = false"
        class="primary-select"
      >
        <div
          @click="handleOpenSelect"
          :class="{ open: selectIsOpen }"
          class="selected"
          tabindex="0" 
        >
          <span>
            {{ selected }}
          </span>
        </div>

        <div class="items" :class="{ selectHide: !selectIsOpen }">
          <div
            v-for="option in optionsList"
            :key="option.id"
            @click="handleSelectOption(option)"
          >
            {{ option.name }}
          </div>
        </div>
      </div>
    </layout>
  </div>
</template>

<script>
import Layout from './Layout.vue'

export default {
  name: 'piymary-select',

  components: {
    Layout,
  },

  props: {
    options: {
      type: Array,
      required: true,
    },
    label: {
      type: String,
      required: true,
    },
  },

  data() {
    return {
      selected: null,
      selectIsOpen: false,
    };
  },

  methods: {
    handleSelectOption({ name, id }) {
      this.selected = name;
      this.selectIsOpen = false;
      this.$emit('input', id);
    },

    handleOpenSelect() {
      this.selectIsOpen = !this.selectIsOpen;
      this.selected = '';
      this.$emit('input', null);
    },
  },

  computed: {
    optionsList() {
      return [{ name: '' }, ...this.options]
    },
  },
};
</script>