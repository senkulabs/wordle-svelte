<script>
    import { sample } from "../utils";
    import { WORDS } from "../data";
    import GuessInput from "./GuessInput.svelte";
    import GuessResults from "./GuessResults.svelte";
    import { checkGuess } from "../game-helpers";
    import { NUM_OF_GUESSES_ALLOWED } from "../constants";

    // Pick a random word on every pageload.
    const answer = sample(WORDS);
    console.info({ answer });

    let guesses = $state([]);

    // Game status: running | win | lose
    // Running: guesses.length < 6 and user incorrect answer the guess
    // Win: guesses.length <= 6 and user correct answer the guess
    // Lose: guesses.length == 6 and user incorrect answer the guess
    let gameStatus = $state('running');

    function handleGuessInput(guess) {
        if (guess === answer) {
            gameStatus = 'win';
        }
        const updatedGuess = checkGuess(guess, answer);
        const updatedGuesses = [...guesses, updatedGuess];
        if (updatedGuesses.length === NUM_OF_GUESSES_ALLOWED) {
            if (guess === answer) {
                gameStatus = 'win';
            } else {
                gameStatus = 'lose';
            }
        }
        guesses.push(updatedGuess);
    }
</script>

<GuessResults guesses={guesses}/>
<GuessInput gameStatus={gameStatus} handleGuessInput={handleGuessInput}/>
{#if gameStatus === 'win'}
    <div class="happy banner">
        <p>
            <strong>Congratulations!</strong> Got it in <strong>{guesses.length} {guesses.length > 1 ? 'guesses' : 'guess'}</strong>
        </p>
    </div>
{/if}
{#if gameStatus === 'lose'}
    <div class="sad banner">
        <p>
            Sorry, the correct answer is <strong>{answer}</strong>
        </p>
    </div>
{/if}