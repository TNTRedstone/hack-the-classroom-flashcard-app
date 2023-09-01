<script>
	let flashcardLists = ["None selected currently"];
</script>

<main>
	{#each flashcardLists as flashcardList}
		<select>
			<option value={flashcardList}>{flashcardList}</option>
		</select>
	{/each}
</main>

<style></style>