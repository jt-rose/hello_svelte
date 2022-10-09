<script lang="ts">
    let cats = ["Meowgli", "Purrkins", "MoMo"]
    let editing = ""
    const setEditing = (target: string) => {
        editing = target
    }

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

    const adoptCat = (name: string) => {
        cats = cats.filter(n => n !== name)
    }

    const updateCat = (oldName: string) => (e: any) => {
        const formData = new FormData(e.target);

    const data: any = {};
    for (let field of formData) {
      const [key, value] = field;
      data[key] = value;
    }

        cats = cats.map(c => c === oldName ? data.update : c)
    }
</script>

<h2>Cats</h2>
<ul>
{#each cats as cat}
{#if cat === editing}
<form on:submit|preventDefault={updateCat(cat)}>
    <label for="name">New Name</label>
    <input type="text" name="update" id="cat-name-edit" value={cat}/>
    <button type="submit" >Change Name</button>
</form>
{:else}
<li>{cat}</li> <div on:click={() => setEditing(cat)}>Update</div><div on:click={() => adoptCat(cat)}>X</div>
{/if}
{/each}
</ul>

<form on:submit|preventDefault={addCat}>
    <label for="name">Cat Name</label>
    <input type="text" name="name" id="cat-name" value=""/>
    <button type="submit" >Add a Cat</button>
</form>