<script>
    import { createEventDispatcher } from "svelte";
    let dispatch = createEventDispatcher();
    let flashcardLists = [{ name: "None selected currently", data: [] }];
    let newFlashcardListName = "";
    let selectedListIndex = 0;
    let newCardFront = "";
    let newCardBack = "";

    dispatch("sendFlashcardLists", flashcardLists[selectedListIndex]);

    function addFlashcardList() {
        if (newFlashcardListName.trim() !== "") {
            flashcardLists.push({ name: newFlashcardListName, data: [] });
            selectedListIndex = flashcardLists.length - 1;
            newFlashcardListName = "";
        }
        sendFlashcardLists();
    }

    function addCard() {
        if (newCardFront.trim() !== "" && newCardBack.trim() !== "") {
            let newCard = {
                front: newCardFront,
                back: newCardBack,
                completed: false
            };
            flashcardLists[selectedListIndex].data.push(newCard);
            newCardFront = "";
            newCardBack = "";
        }
        sendFlashcardLists();
    }

    function sendFlashcardLists() {
        dispatch("sendFlashcardLists", flashcardLists[selectedListIndex]);
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
        <input type="text" placeholder="front of card" bind:value={newCardFront} />
        <input type="text" placeholder="back of card" bind:value={newCardBack} />
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
