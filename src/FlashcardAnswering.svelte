<script>
    import Card from "./Card.svelte";
    import FlashcardListPicker from "./FlashcardListPicker.svelte";
    let flashcardData = null; // Initialize it with a default value or null

    function getFlashcardData(e) {
        flashcardData = e.detail;
        console.log(flashcardData);
        localStorage.setItem("flashcardData", JSON.stringify(flashcardData));
    }
</script>

<main>
    <FlashcardListPicker on:sendFlashcardLists={getFlashcardData} />
    {#if flashcardData}
        <div id="cardlocation">
            <Card/>
        </div>
    {:else}
        <p>No flashcard data available.</p>
    {/if}
</main>