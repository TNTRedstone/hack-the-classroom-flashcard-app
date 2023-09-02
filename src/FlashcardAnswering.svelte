<script>
    import FlashcardListPicker from "./FlashcardListPicker.svelte";
    import Card from "./Card.svelte";
    
    let flashcardData = []; // Initialize an array to store the flashcard data
    
    const handleNewCard = (e) => {
        flashcardData = e.detail; // Update the flashcardData array when a new card is added
    };
</script>

<main>
    <FlashcardListPicker on:handleNewCard={handleNewCard}></FlashcardListPicker>
    
    {#if flashcardData.length > 0}
        {#each flashcardData as card, index (card.id)}
            <Card front={card.front} back={card.back}></Card>
        {/each}
    {/if}
</main>
