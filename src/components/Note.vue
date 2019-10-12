<template>
<div class="ui centered card box-shadow">
    <div class="content" v-show="!showEditForm">
        <div class="header">{{ note.title }}</div>
        <div class="description">
        <p>{{ note.description }}</p>
        </div>
    </div>
    <div class="extra content">
        <span class="left floated like" v-on:click="showForm">
        <i class="edit icon"></i>
        Edit
        </span>
        <span class="right floated star" v-on:click="deleteNote(note)">
        <i class="trash icon"></i>
        Delete
        </span>
    </div>

    <div class="content" v-show="showEditForm">
      <div class='ui form'>
        <div class='field'>
          <label>Title</label>
          <input type='text' v-model="note.title" >
        </div>
        <div class='field'>
          <label>Description</label>
          <textarea name="" v-model="note.description" rows="5"></textarea>
        </div>
        <div class='ui two buttons'>
          <button class='ui red button' v-on:click="hideForm">
            Tutup
          </button>
        </div>
      </div>
    </div>
</div>
  
</template>

<script type="text/javascript">
  export default {
    props: ['note'],
    data() {
      return {
        showEditForm: false,
      };
    },
    methods: {
      deleteNote(note) {
        this.$emit('delete-note', note);
      },
      showForm() {
        this.showEditForm = true;
      },
      hideForm() {
        this.showEditForm = false;
      },
    },
  };
</script>

<style scoped>
  .italic {font-style: italic}
  .box-shadow{
        background-color: #ffffff; box-shadow: 0px 8px 24px 0 rgba(0,0,0,0.1);
        border:1px solid #fafafa;
    }
</style>