<template>
  <div class='ui basic content segment'>
    <div class='ui centered card box-shadow' style="background-color: #ffffff; box-shadow: 0px 8px 24px 0 rgba(0,0,0,0.1); border:1px solid #f8f8f8;">
      <div class='content'>
        <div class='ui form'>
          <div class='field'>
            <input v-model="titleText" type='text' placeholder="Title">
          </div>
          <div class='field'>
            <textarea  v-model="descriptionText" name="" id="" cols="20" rows="5" placeholder="Description"></textarea>
            <!-- <input type='text'> -->
          </div>
          <div class='ui buttons' style="float:right;">
            <button class='ui green button' v-on:click="sendForm()">
              OK
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titleText: '',
      descriptionText: '',
      isCreating: false,
    };
  },
  methods: {
    openForm() {
      this.isCreating = true;
    },
    closeForm() {
      this.isCreating = false;
    },
    sendForm() {
      if (this.titleText.length > 0 && this.descriptionText.length > 0) {
        const title = this.titleText;
        const description = this.descriptionText;
        this.$emit('create-note', {
          title,
          description,
        });
        this.titleText = '';
        this.descriptionText = '';
        this.isCreating = false;
      }
    },
  },
};
</script>
<style scoped>
  .box-shadow{
        background-color: #ffffff; box-shadow: 0px 8px 24px 0 rgba(0,0,0,0.1);
        border:1px solid #fafafa;
    }
</style>