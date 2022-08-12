<template>
  <base-dialog title="Invalid Inputs" v-if="inValid" @close="inValid = false">
    <template #default>
      <p>Sorry, You have to fill the form</p>
    </template>
    <template #actions>
      <base-button @click="inValid = false">Okay</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title:</label>
        <input type="text" name="title" id="title" v-model="title" />
      </div>
      <div class="form-control">
        <label for="descri">Description:</label>
        <textarea
          name="descri"
          id="descri"
          rows="3"
          v-model="description"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link:</label>
        <input type="text" name="link" id="link" v-model="link" />
      </div>
      <div>
        <base-button type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
</template>
<script>
export default {
  inject: ["addRes"],
  data() {
    return {
      title: "",
      description: "",
      link: "",
      inValid: false,
    };
  },
  methods: {
    resetInputs() {
      this.title = "";
      this.description = "";
      this.link = "";
    },
    submitData() {
      if (
        this.title.trim() == "" ||
        this.description.trim() == "" ||
        this.link.trim() == ""
      ) {
        this.inValid = true;
      } else {
        this.addRes(this.title, this.description, this.link);
        this.resetInputs();
      }
    },
  },
};
</script>
<style>
label {
  @apply font-bold mt-2;
}
input,
textarea {
  @apply w-full p-[0.15rem] border border-[#ccc] focus:outline-none focus:border-[#3a0061] focus:bg-[#f7ebff];
}
.form-control {
  @apply my-4;
}
</style>
