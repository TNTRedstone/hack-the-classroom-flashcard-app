<script>
    let flashcardLists = ["None selected currently"];
    let newFlashcardListName = "";
    let selectedList = "None selected currently";

    function addFlashcardList() {
        if (newFlashcardListName.trim() !== "") {
            flashcardLists = [...flashcardLists, newFlashcardListName];
            selectedList = newFlashcardListName; // Select the newly added option
            newFlashcardListName = ""; // Clear the input field after adding
        }
    }
</script>

<main>
    <select bind:value={selectedList}>
        {#each flashcardLists as flashcardList}
            <option value={flashcardList}>{flashcardList}</option>
        {/each}
    </select>
    <input bind:value={newFlashcardListName} type="text" />
    <button on:click={addFlashcardList}>Add</button>
</main>

<style></style>
