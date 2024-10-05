<script>
    export let deleteNote;
    export let noteId;
</script>

<button
    class="bg-red-500 text-white px-4 py-2 rounded hover:bg-red-600 ml-auto"
    on:click={() => deleteNote(noteId)}
>
    Delete
</button>