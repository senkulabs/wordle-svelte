<script>
    import { sample } from "../utils";
    import { WORDS } from "../data";
    import GuessInput from "./GuessInput.svelte";

    // Pick a random word on every pageload.
    const answer = sample(WORDS);
    console.info({ answer });
</script>

<GuessInput/>