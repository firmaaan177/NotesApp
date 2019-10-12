<template>
  <div id="app">
    <h1 class="ui centered header" style="margin-top:30px;">Notes App</h1>
    <div>
      <create-note v-on:create-note="createNote"></create-note>
      <list-notes v-bind:notes="notes"></list-notes>
    </div>
  </div>
</template>

<script>
  import ListNotes from './components/ListNotes';
  import CreateNote from './components/CreateNotes';
  export default {
    name: 'app',
    components: {
      ListNotes,
      CreateNote,
    },
    data() {
      return {
        notes: [{
          title: 'My Title 1',
          description: 'Description 1.'
        }, {
          title: 'My Title 2',
          description: 'Description 2.'
        }, {
          title: 'My Title 2',
          description: 'Description 3.'
        }],
      };
    },
    methods: {
      createNote(note) {
        this.notes.push(note);
        alert('Note created!');
      },
    },
  };
</script>