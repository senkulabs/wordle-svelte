<script>
    import { sample } from "../utils";
    import { WORDS } from "../data";
    import GuessInput from "./GuessInput.svelte";
    import GuessResults from "./GuessResults.svelte";
    import { guesses } from "../guesses.svelte";
    import { checkGuess } from "../game-helpers";

    // Pick a random word on every pageload.
    const answer = sample(WORDS);
    console.info({ answer });

    function handleGuessInput(guess) {
        const updatedGuess = checkGuess(guess, answer);
        guesses.push(updatedGuess);
    }
</script>

<GuessResults guesses={guesses}/>
<GuessInput handleGuessInput={handleGuessInput}/>