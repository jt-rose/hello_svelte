<script lang="ts">
    let cats = ["Meowgli", "Purrkins", "MoMo"]
    
    let editing = ""
    const setEditing = (target: string) => {
        editing = target
        editCatInput = target
    }


    let addCatInput = ""
    const setAddCatInput = (e: any) => {
        addCatInput = e.target.value
    }

    let editCatInput = ""
    const setEditCatInput = (e: any) => {
        editCatInput = e.target.value
    }


    const addCat = (e: any) => {
        if (!e.target) return
        const formData = new FormData(e.target);

    const data: any = {};
    for (let field of formData) {
      const [key, value] = field;
      data[key] = value;
    }
    cats.push(addCatInput)
    cats = cats

    addCatInput = ""
    }

    const adoptCat = (name: string) => {
        cats = cats.filter(n => n !== name)
    }

    const updateCat = () => {
        cats = cats.map(cat => cat === editing ? editCatInput : cat)
        editCatInput = ""
        editing = ""
    }
</script>

<h2>Cats</h2>
<ul>
{#each cats as cat}
{#if cat === editing}
    <label for="name">New Name</label>
    <input type="text" name="update" id="cat-name-edit" value={editCatInput} on:change={setEditCatInput}/>
    <button on:click={updateCat}>Change Name</button>
{:else}
<li>{cat}</li> <div on:click={() => setEditing(cat)}>Update</div><div on:click={() => adoptCat(cat)}>X</div>
{/if}
{/each}
</ul>

<form on:submit|preventDefault={addCat}>
    <label for="name">Cat Name</label>
    <input type="text" name="name" id="cat-name" value={addCatInput} on:change={setAddCatInput}/>
    <button type="submit" >Add a Cat</button>
</form>