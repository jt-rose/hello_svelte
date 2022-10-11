<script lang="ts">
    import { counter } from "../stores/counterStore"

    let counterValue = 1

    counter.subscribe(value => {
        counterValue = value
    })

    const double = () => {
        counter.update(num => num * 2)
    }

    const halve = () => {
        counter.update(num => num / 2)
    }

    const reset = () => {
        counter.set(1)
    }
</script>

<div>
    <h1>{counterValue}</h1>
    <p>Counter value from svelte store</p>
    <button on:click={double}>Double</button>
    <button on:click={halve}>Halve</button>
    <button on:click={reset}>Reset</button>
</div>