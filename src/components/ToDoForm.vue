<template>
  <div>
    <form @submit.prevent="onSubmit">
      <label for="new-todo-input">What New Today? </label>
      <input
        type="text"
        id="new-todo-input"
        name="new-todo"
        autocomplete="off"
        v-model.lazy.trim="label"
      />
      <button type="submit">Add</button>
    </form>
  </div>
</template>

<script>
export default {
  methods: {
    onSubmit() {
      if(this.label === ''){
          return;
      }
      this.$emit('todo-added', this.label);
      this.label = ''
    },
  },
  data() {
    return {
      label: "",
    };
  },
};
</script>
