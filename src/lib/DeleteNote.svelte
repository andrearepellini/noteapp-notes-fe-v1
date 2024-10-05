<script>
    export let deleteNote;
    export let noteId;
</script>

<button
    class="bg-red-500 text-white px-2 py-1 rounded"
    on:click={() => deleteNote(noteId)}
>
    Delete
</button>