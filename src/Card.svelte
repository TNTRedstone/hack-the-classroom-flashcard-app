<script>
    function showInvisableCard() {
        document.querySelector(".visablecard").style.visibility = "hidden";
    }

    function showVisibleCard() {
        document.querySelector(".visablecard").style.visibility = "visable";
    }

    function handleDoneClick() {
        showVisibleCard();
    }

    let front;
    let back;
    function updateFlashcardContent() {
        let flashcardData = JSON.parse(localStorage.getItem("flashcardData")); // Parse the stored data back to an object
        if (flashcardData) {
            for (let i = 0; i < flashcardData.data.length; i++) {
                front = flashcardData.data[i].front;
                back = flashcardData.data[i].back;
            }
            // Update the content of your flashcards here
            try {
                document.getElementById("invisCardText").textContent = back;
                document.getElementById("visCardText").textContent = front;
            } catch (e) {
                null;
            }
        }
    }

    // Update flashcard content initially and set an interval to periodically check for updates
    updateFlashcardContent();
    setInterval(updateFlashcardContent, 5000); // Check every 5 seconds (adjust as needed)
</script>

<main>
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
        href="https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,400;1,900&display=swap"
        rel="stylesheet"
    />
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <div on:click={showVisibleCard} class="invisablecard card">
        <span>
            <h2 id="invisCardText">{back}</h2>
            <button on:click={handleDoneClick}>Done</button>
        </span>
    </div>
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <div on:click={showInvisableCard} class="visablecard card">
        <span>
            <h2 id="invisCardText">{front}</h2>
        </span>
    </div>
</main>

<style>
    main {
        display: relative;
    }

    .card {
        position: absolute;
        width: 350px;
        height: 175px;
        left: 0;
        right: 0;
        top: 0;
        bottom: 0;
        margin-left: auto;
        margin-right: auto;
        margin-top: auto;
        margin-bottom: auto;
        border-radius: 5px;
    }

    .visablecard {
        background-color: #ef2bb8;
        filter: drop-shadow(2px 2px 0.5px #003a61);
    }

    .invisablecard {
        background-color: #003a61;
    }

    h2 {
        user-select: none;
        -moz-user-select: none;
        -khtml-user-select: none;
        -webkit-user-select: none;
        -o-user-select: none;
        font-family: "poppins";
    }
    div {
        display: table;
        height: 100px;
        width: 100%;
        text-align: center;
    }
    span {
        display: table-cell;
        vertical-align: middle;
    }
</style>
