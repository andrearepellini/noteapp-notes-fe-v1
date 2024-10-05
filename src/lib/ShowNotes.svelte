<script>
    import DeleteNote from "./DeleteNote.svelte";
    export let notes = [];
    export let deleteNote;
</script>

<ul>
    {#each notes as note}
        <li class="border p-4 mb-2 flex items-center">
            <div class="flex-grow">
                <h2 class="font-bold">{note.title}</h2>
                <p>{note.content}</p>
            </div>
            <div class="ml-4">
                <DeleteNote {deleteNote} noteId={note.id} />
            </div>
        </li>
    {/each}
</ul>
