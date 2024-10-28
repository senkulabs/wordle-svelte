<script>
    import { sample } from "../utils";
    import { WORDS } from "../data";

    // Pick a random word on every pageload.
    const answer = sample(WORDS);
    console.info({ answer });
</script>

<p>Put a game here!</p>