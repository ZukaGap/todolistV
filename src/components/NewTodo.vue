<template>
  <form class="formTodo" @submit.prevent="addTodo()">
    <input type="text" class="addTodo" v-model="newTodo" placeholder="Enter Todo" />
  </form>
</template>

<script>
export default {
  data() {
    return {
      newTodo: "",
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.length > 1) {
        this.$emit("on-addtodo", this.newTodo);
      }
      this.newTodo = "";
    },
  },
};
</script>

<style scoped>
.formTodo {
  width: 100%;
  margin: auto;
  display: flex;
  justify-content: center;
}

.addTodo {
  position: relative;
  width: 100%;
  height: 45px;
  color: #cdb30c;
  background-color: #535204;
  border: 2px solid transparent;
  border-radius: 100vw;
  box-sizing: border-box;
  padding: 0 15px;
  font-size: 18px;
  outline: none;
}

.addTodo:focus {
  border: 2px solid #cdb30c;
}

.addTodo::placeholder {
  color: #cdb30c;
}
</style>