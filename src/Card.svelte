<script></script>

<main>
    <div class="invisablecard card">
        <h2>side 2</h2>
    </div>
    <div class="visablecard card">
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
</style>
