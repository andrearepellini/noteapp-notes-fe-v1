<!-- CreateNote.svelte -->
<script>
    import { createEventDispatcher } from "svelte";

    export let newNote = { title: "", content: "" };

    const dispatch = createEventDispatcher();

    async function addNote() {
        const response = await fetch("http://localhost:8080/api/notes", {
            method: "POST",
            headers: {
                "Content-Type": "application/json",
            },
            body: JSON.stringify(newNote),
        });

        if (response.ok) {
            const note = await response.json();
            dispatch("noteCreated", note); // Dispatch the created note
            newNote = { title: "", content: "" }; // Reset the input fields
        } else {
            alert("Failed to add note. Please try again."); // Handle potential errors
        }
    }
</script>

<div class="mb-4">
    <input
        bind:value={newNote.title}
        placeholder="Title"
        class="border rounded p-2 w-full mb-2"
    />
    <textarea
        bind:value={newNote.content}
        placeholder="Content"
        class="border rounded p-2 w-full"
    ></textarea>
    <button
        on:click={addNote}
        class="bg-blue-500 text-white px-4 py-2 rounded mt-2"
    >
        Add Note
    </button>
</div>
