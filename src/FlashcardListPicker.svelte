<script>
    let flashcardLists = [{ name: "None selected currently", data: [] }];
    let newFlashcardListName = "";
    let selectedListIndex = 0; // Initialize with the index of the default list
    let newCardFront = "";
    let newCardBack = "";

    function addFlashcardList() {
        if (newFlashcardListName.trim() !== "") {
            flashcardLists.push({ name: newFlashcardListName, data: [] });
            selectedListIndex = flashcardLists.length - 1; // Select the newly added option
            newFlashcardListName = ""; // Clear the input field after adding
        }
    }

    function addCard() {
        if (newCardFront.trim() !== "" && newCardBack.trim() !== "") {
            let newCard = {
                front: newCardFront,
                back: newCardBack,
            };
            flashcardLists[selectedListIndex].data.push(newCard);
            newCardFront = "";
            newCardBack = "";
        }
    }
</script>

<main>
    <select bind:value={selectedListIndex}>
        {#each flashcardLists as flashcardList, index}
            <option value={index}>{flashcardList.name}</option>
        {/each}
    </select>
    <div>
        <input bind:value={newFlashcardListName} type="text" />
        <button on:click={addFlashcardList}>Add</button>
    </div>
    <div>
        <input type="text" placeholder="front of card" bind:value={newCardFront}>
        <input type="text" placeholder="back of card" bind:value={newCardBack}>
        <button on:click={addCard}>Add</button>
    </div>
</main>

<style>
    main {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    button {
        user-select: none;
    }
</style>
