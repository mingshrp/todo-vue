<template>
  <div class="stack-small" v-if="!isEditing">
    <div class="custom-checkbox">
      <input
        type="checkbox"
        class="checkbox"
        :id="id"
        :checked="isDone"
        @change="$emit('checkbox-changed')"
      />
      <label :for="id" class="checkbox-label">{{ label }}</label>
    </div>

    <div class="btn-group">
      <button type="button" class="btn" @click="toggleToItemEditForm">
        Edit <span class="visually-hidden">{{ label }}</span>
      </button>
      <button type="button" class="btn btn__danger" @click="deleteToDo">
        Delete <span class="visually-hidden">{{ label }}</span>
      </button>
    </div>
  </div>

  <to-do-item-edit-form
    v-else
    :id="id"
    :label="label"
    @item-edited="itemEdited"
    @edit-cancelled="editCancelled"
  />
</template>

<script>
import ToDoItemEditForm from "./ToDoItemEditForm.vue";

export default {
  name: "ToDoItem",
  components: {
    ToDoItemEditForm,
  },
  props: {
    label: String,
    done: Boolean,
    id: String,
  },
  data() {
    return {
      isEditing: false,
    };
  },
  computed: {
    isDone() {
      return this.done;
    },
  },
  methods: {
    deleteToDo() {
      this.$emit("item-deleted");
    },
    toggleToItemEditForm() {
      this.isEditing = true;
    },
    itemEdited(newLabel) {
      this.$emit("item-edited", newLabel);
      this.isEditing = false;
    },
    editCancelled() {
      this.isEditing = false;
    },
  },
};
</script>

<style scoped>
.stack-small {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  padding: 0.8rem 0;
  border-bottom: 1px solid #ffc8dc;
}

.custom-checkbox {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.checkbox {
  accent-color: #ff7ab8;
  width: 1.6rem;
  height: 1.6rem;
  cursor: pointer;
}

.checkbox-label {
  font-size: 1.6rem;
  color: #4d4d4d;
  user-select: none;
}

.btn-group {
  display: flex;
  gap: 1rem;
}

.btn {
  background-color: #ff9fcf;
  color: white;
  border: none;
  padding: 0.5em 1em;
  border-radius: 6px;
  cursor: pointer;
  transition: background 0.2s ease, transform 0.1s ease;
}

.btn:hover {
  background-color: #ff7ab8;
  transform: scale(1.03);
}

.btn__danger {
  background-color: #ff6b8a;
}

.btn__danger:hover {
  background-color: #ff4778;
}
</style>
