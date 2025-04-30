<template>
  <base-dialog
    v-if="inputIsInvalid"
    title="Invalid Input"
    @close="confirmError"
  >
    <template #default>
      <p>All inputs are required!</p>
      <p>At least one input value is invalid.</p>
      <p>Please check the submition form and try again</p>
    </template>
    <template #actions>
      <base-btn @click="confirmError">I understand</base-btn>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-controll">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" ref="titleInput" />
      </div>
      <div class="form-controll">
        <label for="description">Description</label>
        <textarea
          id="description"
          name="description"
          rows="3"
          ref="descInput"
        ></textarea>
      </div>
      <div class="form-controll">
        <label for="link">Link</label>
        <input id="link" name="link" type="url" ref="linkInput" />
      </div>
      <div>
        <base-btn type="submit">Add Resource</base-btn>
      </div>
    </form>
  </base-card>
</template>

<script>
  export default {
    inject: ['addResource'],
    data() {
      return {
        inputIsInvalid: false,
      };
    },
    methods: {
      submitData() {
        const enteredTitle = this.$refs.titleInput.value;
        const enteredDesc = this.$refs.descInput.value;
        const enteredLink = this.$refs.linkInput.value;

        if (
          enteredTitle.trim() === '' ||
          enteredDesc.trim() === '' ||
          enteredLink.trim() === ''
        ) {
          this.inputIsInvalid = true;
          return;
        }
        this.addResource(enteredTitle, enteredDesc, enteredLink);
      },
      confirmError() {
        this.inputIsInvalid = false;
      },
    },
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
    padding: 0.15rem;
    border: 1px solid #ccc;
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
