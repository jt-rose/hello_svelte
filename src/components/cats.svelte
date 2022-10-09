<script lang="ts">
    let cats = ["Meowgli", "Purrkins", "MoMo"]

    const addCat = (e: any) => {
        if (!e.target) return
        const formData = new FormData(e.target);

    const data: any = {};
    for (let field of formData) {
      const [key, value] = field;
      data[key] = value;
    }
    cats.push(data.name)
    cats = cats
    }
</script>

<h2>Cats</h2>
<ul>
{#each cats as cat}
<li>{cat}</li>
{/each}
</ul>

<form on:submit|preventDefault={addCat}>
    <label for="name">Cat Name</label>
    <input type="text" name="name" id="cat-name" value=""/>
    <button type="submit" >Add a Cat</button>
</form>