<script>
    let { guesses } = $props();
    import { NUM_OF_GUESSES_ALLOWED } from "../constants";
    import { range } from "../utils";
    import Guess from "./Guess.svelte";
</script>

<div class="guess-results">
    {#each range(NUM_OF_GUESSES_ALLOWED) as row}
        <Guess guess={guesses[row]} />
    {/each}
</div>