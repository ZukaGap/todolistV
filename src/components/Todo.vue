<template>
  <li class="list">
    <div>
      <button
        class="string"
        v-if="!isEditing"
        :class="{completed}"
        @click="$emit('on-toggle')"
      >{{todoString}}</button>
      <form v-else @submit.prevent="endEditing()">
        <input @blur="startEditing()" v-model="newTodoString" type="text" />
      </form>
    </div>
    <div>
      <button class="edit" @click="startEditing()">Edit</button>
      <button class="delete" @click="$emit('on-delete')">Delete</button>
    </div>
  </li>
</template>

<script>
export default {
  props: {
    todoString: String,
    completed: Boolean,
  },
  data() {
    return {
      isEditing: false,
      newTodoString: "",
    };
  },
  methods: {
    startEditing() {
      if (!this.isEditing) {
        this.newTodoString = this.todoString;
        this.isEditing = true;
      } else {
        this.endEditing();
      }
    },
    endEditing() {
      this.isEditing = false;
      this.$emit("on-edit", this.newTodoString);
    },
  },
};
</script>

<style scoped>
.completed {
  text-decoration: line-through;
}

.list {
  width: 100%;
  height: 40px;
  list-style-type: none;
  margin: 0.2rem 0;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

.list .string {
  width: 200px;
  overflow: auto;
  overflow-y: hidden;
}

.list button {
  height: 30px;
  width: auto;
  margin: 0 0.2rem;
  color: #cdb30c;
  background-color: transparent;
  border-color: transparent;
  border-radius: 4px;
  outline: none;
  font-size: 18px;
}

.list .list .edit {
  color: #cd690c;
  border: 2px solid #cd690c;
}

.list .delete {
  color: #cd390c;
  border: 2px solid #cd390c;
}

.list input {
  height: 30px;
  margin: 0 0.2rem;
  font-size: 18px;
  border: transparent;
  background-color: transparent;
  color: #cdb30c;
  border-bottom: 2px solid #cd690c;
  caret-color: #cd690c;
  outline: none;
}

/* width */
::-webkit-scrollbar {
  width: 10px;
  height: 3px;
}

/* Track */
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px grey;
  border-radius: 10px;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: #535204;
  border-radius: 10px;
}
</style>