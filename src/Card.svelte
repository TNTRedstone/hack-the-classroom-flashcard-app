<script>
    function showInvisableCard() {
        document.querySelector(".visablecard").style.display = "none";
    }
    function showVisableCard() {
        document.querySelector(".visablecard").style.display = "block";
    }
</script>

<main>
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <div on:click={showVisableCard} class="invisablecard card">
        <h2>side 2</h2>
    </div>
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <div on:click={showInvisableCard} class="visablecard card">
        <h2>side 1</h2>
    </div>
</main>

<style>
    main {
        display: relative;
    }

    .card {
        position: absolute;
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
    }
</style>
