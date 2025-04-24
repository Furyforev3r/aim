<script lang="ts">
    import Icon from "@iconify/svelte"
    let text = "Start Training"
    let times: number[] = []
    let waiting = false
    let started = false
    let startTime = 0
    let timeoutId: any
    let attempts = 0
    const maxAttempts = 5
    let showResults = false

    function startNextAttempt() {
        if (attempts >= maxAttempts) {
            showResults = true
            text = "Test completed! Click to see results."
            return
        }

        text = "Wait for it..."
        started = true

        const delay = Math.random() * 2000 + 1000
        timeoutId = setTimeout(() => {
            waiting = true
            startTime = performance.now()
            text = "CLICK!"
        }, delay)
    }

    function handleClick() {
        if (showResults) {
            resetAll()
            return
        }

        if (!started) {
            startNextAttempt()
        } else if (waiting) {
            const reactionTime = performance.now() - startTime
            times = [...times, Math.round(reactionTime)]
            attempts++
            reset()
            startNextAttempt()
        } else {
            clearTimeout(timeoutId)
            times = [...times, 1000]
            attempts++
            text = "Too Soon! Click to continue. (1s penalty)"
            started = false
        }
    }

    function reset() {
        waiting = false
        started = false
    }

    function resetAll() {
        waiting = false
        started = false
        text = "Start Training"
        times = []
        attempts = 0
        showResults = false
    }

    $: averageTime = times.length > 0 ? Math.round(times.reduce((a, b) => a + b, 0) / times.length) : 0
</script>

<svelte:head>
	<title>Aim - Reflexes</title>
	<meta name="description" content="Aim trainer" />
</svelte:head>

<div class="app">
    <h1>Reflexes Training!</h1>
    {#if showResults}
        <div class="results">
            <h2>Results</h2>
            <p>Reaction times: <strong>{times.join(", ")} ms</strong></p>
            <p>Average time: <strong>{averageTime} ms</strong></p>
            <button class="restart" on:click={resetAll}><Icon icon="mdi:restart" width="24" height="24" />Restart</button>
        </div>
    {:else}
        <p>Attempts: {attempts} / {maxAttempts}</p>
        <button
            class="reflex"
            on:click={handleClick}
            on:contextmenu={handleClick}
            class:active={waiting}
        >
            {text}
        </button>
        <p>Latest time: {times.length > 0 ? `${times[times.length - 1]} ms` : "N/A"}</p>
    {/if}
</div>

<style>
    .app {
        margin: 3rem;
        display: grid;
        place-items: center;
        gap: 1rem;
        text-align: center;
        color: var(--text-color);
    }

    .reflex {
        cursor: pointer;
        font-size: 1.2rem;
        font-weight: bold;
        color: var(--text-color);
        background-color: var(--button-background);
        border-radius: 0.3rem;
        border: 1px solid var(--blue-primary-color);
        width: 400px;
        height: 400px;
    }

    button.active {
        background-color: var(--blue-primary-color);
    }
    .results {
        padding: 1rem;
        border-radius: 0.3rem;
        background-color: var(--input-background);
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        gap: 1rem;
        opacity: 0;
        animation: fadeIn 0.3s ease-in-out forwards;
    }

    @keyframes fadeIn {
        from {
            opacity: 0;
        }
        to {
            opacity: 1;
        }
    }

    .restart {
        display: flex;
        flex: row;
        align-items: center;
        justify-content: center;
        gap: 1rem;
        cursor: pointer;
        font-size: 1.2rem;
        font-weight: bold;
        color: var(--text-color);
        background-color: var(--button-background);
        border-radius: 0.3rem;
        border: 1px solid var(--blue-primary-color);
        padding: 1rem 2rem;
    }
    
    @media (max-width: 600px) {
        .reflex {
            width: 100%;
            height: 300px;
        }
        
		.app {
			align-items: center;
		}
    }
</style>
