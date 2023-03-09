<template>
  <base-dialog
    v-if="inputIsInvalid"
    title="Invalid Input"
    @close="confirmErrorMsg"
  >
    <template #default>At least one input value is invalid</template>
    <template #actions>
      <base-button @click="confirmErrorMsg()">Okay</base-button>
    </template>
  </base-dialog>

  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" id="title" ref="titleInput" v-model="title" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          type="text"
          id="description"
          name="description"
          rows="4"
          ref="descriptionInput"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input type="url" id="link" name="link" ref="linkInput" />
      </div>
      <div class="form-control">
        <base-button type="submit">Resource</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
import BaseButton from "../UI/BaseButton.vue";
import BaseDialog from "../UI/BaseDialog.vue";
export default {
  components: { BaseDialog, BaseButton },
  data() {
    return {
      inputIsInvalid: false,
    };
  },
  methods: {
    submitData() {
      const enteredTitle = this.$refs.titleInput.value;
      const enteredDescription = this.$refs.descriptionInput.value;
      const enteredLink = this.$refs.linkInput.value;

      if (
        enteredTitle.trim() === "" ||
        enteredDescription.trim() === "" ||
        enteredLink.trim() === ""
      ) {
        this.inputIsInvalid = true;
      } else {
        this.addResource(enteredTitle, enteredDescription, enteredLink);
      }
    },
    confirmErrorMsg() {
      this.inputIsInvalid = false;
    },
  },
  inject: ["addResource"],
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.2rem;
  border: 1px solid #ccc;
  border-radius: 5px;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
