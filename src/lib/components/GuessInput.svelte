<script>
    let { handleGuessInput } = $props();
    let guess = $state('');

    function handleSubmit(event) {
        event.preventDefault();
        handleGuessInput(guess);
        guess = '';
    }
</script>

<form onsubmit={handleSubmit} class="guess-input-wrapper">
    <label for="guess-input">Enter guess:</label>
    <input required type="text" id="guess-input" minlength="5" maxlength="5" pattern={`[A-Z]{5}`} title="5 letter word" bind:value={guess} oninput={(event) => {
        guess = event.target.value.toUpperCase();
    }}>
</form>