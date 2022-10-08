<script>
    let clicked = 0;
    const addOnClick = () => {
        clicked++
    }

    const minusOnClick = () => {
        clicked--
    }
</script>

<p>Clicked {clicked} times</p>
<button on:click={minusOnClick}>-</button>
<button on:click={addOnClick}>+</button>