<script>
    import { sample } from "../utils";
    import { WORDS } from "../data";
    import GameInput from "./GameInput.svelte";

    // Pick a random word on every pageload.
    const answer = sample(WORDS);
    console.info({ answer });
</script>

<GameInput/>