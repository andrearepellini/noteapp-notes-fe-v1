<script>
    import DeleteNote from "./DeleteNote.svelte";
    export let notes = [];
    export let deleteNote;
</script>

<ul>
    {#each notes as note}
        <li class="border p-4 mb-2">
            <div>
                <h2 class="font-bold">{note.title}</h2>
                <p>{note.content}</p>
            </div>
            <DeleteNote {deleteNote} noteId={note.id} />
        </li>
    {/each}
</ul>
