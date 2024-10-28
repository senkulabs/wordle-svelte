<script>
    let { guesses } = $props();
</script>

<div class="guess-results">
    {#each guesses as guess}
        <p class="guess">{guess}</p>
    {/each}
</div>