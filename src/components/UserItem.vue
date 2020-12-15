<template>
  <div>
    <p>Id: {{ id }}</p>
    <p>FullName: {{ fullName }}</p>
    <p>Age: {{ age }}</p>
    <button @click="removeUser">Remove User</button>
  </div>
</template>

<script>
import { computed } from 'vue';

export default {
  props: {
    id: { type: Number, required: true },
    firstName: { type: String, required: true },
    lastName: { type: String, required: true },
    age: { type: Number, required: true },
  },
  emits: ["delete-user"],
  setup(props, context) {
    const fullName = computed(() => `${props.firstName} ${props.lastName}`);

    function removeUser() {
      context.emit("delete-user", props.id);
    }

    return {
      fullName,
      removeUser,
    };
  },
};
</script>

<style scoped>
div {
  border-radius: 20px;
  border: 1px solid grey;
  margin: 2rem;
}
button {
  background-color: rgb(241, 154, 154);
  color: white;
  font-weight: bold;
}
</style>