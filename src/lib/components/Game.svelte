<script>
    import { sample } from "../utils";
    import { WORDS } from "../data";
    import GuessInput from "./GuessInput.svelte";
    import GuessResults from "./GuessResults.svelte";
    import { guesses } from "../guesses.svelte";

    // Pick a random word on every pageload.
    const answer = sample(WORDS);
    console.info({ answer });

    function handleGuessInput(guess) {
        guesses.push(guess);
    }
</script>

<GuessResults guesses={guesses}/>
<GuessInput handleGuessInput={handleGuessInput}/>