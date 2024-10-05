<script>
  import { onMount } from 'svelte';
  import CreateNote from './lib/CreateNote.svelte';
  import ShowNotes from './lib/ShowNotes.svelte';

  let notes = [];
  let newNote = { title: '', content: '' };

  async function fetchNotes() {
    const response = await fetch('http://localhost:8080/api/notes/all');
    notes = await response.json();
  }

  async function deleteNote(id) {
    await fetch(`http://localhost:8080/api/notes/${id}`, {
      method: 'DELETE',
    });
    notes = notes.filter(note => note.id !== id);
  }

  onMount(fetchNotes); // Fetch notes when the component mounts

  function handleNoteCreated(event) {
    notes = [...notes, event.detail]; // Add the created note to the list
  }
</script>

<div class="container mx-auto">
  <h1 class="text-2xl font-bold mb-4">📝 Note Taking App</h1>
  
  <CreateNote bind:newNote on:noteCreated={handleNoteCreated} />
  <ShowNotes {notes} {deleteNote}/>
</div>

