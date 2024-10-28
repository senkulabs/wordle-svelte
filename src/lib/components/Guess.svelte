<script>
    let { guess } = $props();
    import { range } from "../utils";
    import { NUM_OF_LETTER } from "../constants";
</script>

<p class="guess">
    {#each range(NUM_OF_LETTER) as cell}
        <span class="cell">{guess ? guess[cell] : ''}</span>
    {/each}
</p>