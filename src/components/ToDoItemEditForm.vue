<template>
  <form class="stack-small" @submit.prevent="onSubmit">
    <div>
      <label class="edit-label">Edit Name for "{{ label }}"</label>
      <input
        :id="id"
        type="text"
        autocomplete="off"
        v-model.lazy.trim="newLabel"
      />
    </div>

    <div class="btn-group">
      <button type="button" class="btn" @click="onCancel">
        Cancel
        <span class="visually-hidden">editing {{ label }}</span>
      </button>
      <button type="submit" class="btn btn__primary">
        Save
        <span class="visually-hidden">edit for {{ label }}</span>
      </button>
    </div>
  </form>
</template>

<script>
export default {
  name: "ToDoItemEditForm",
  props: {
    label: {
      type: String,
      required: true,
    },
    id: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      newLabel: this.label,
    };
  },
  methods: {
    onSubmit() {
      if (this.newLabel && this.newLabel !== this.label) {
        this.$emit("item-edited", this.newLabel);
      }
    },
    onCancel() {
      this.$emit("edit-cancelled");
    },
  },
};
</script>

<style scoped>
.edit-label {
  font-family: "Arial", sans-serif;
  color: #0b0c0c;
  display: block;
  margin-bottom: 5px;
}

input {
  display: inline-block;
  margin-top: 0.4rem;
  width: 100%;
  min-height: 4.4rem;
  padding: 0.4rem 0.8rem;
  border: 2px solid #565656;
  border-radius: 4px;
}

form {
  display: flex;
  flex-direction: column;
  gap: 0.8rem;
}

.btn-group {
  display: flex;
  gap: 1rem;
}

.btn {
  background-color: #ff9fcf;
  color: white;
  border: none;
  padding: 0.6em 1.2em;
  border-radius: 6px;
  cursor: pointer;
}

.btn:hover {
  background-color: #ff7ab8;
}
</style>
