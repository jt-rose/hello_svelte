<script>
    let name = "Jeff"
    let clicked = 0;
    const addOnClick = () => {
        clicked++
    }

    const minusOnClick = () => {
        clicked--
    }
</script>

<h1>Welcome {name}</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
<p>Clicked {clicked} times</p>
<button on:click={minusOnClick}>-</button>
<button on:click={addOnClick}>+</button>