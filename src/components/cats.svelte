<script>
    let cats = ["Meowgli", "Purrkins", "MoMo"]
</script>

<h2>Cats</h2>
<ul>
{#each cats as cat}
<li>{cat}</li>
{/each}
</ul>