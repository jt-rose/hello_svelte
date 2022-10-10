<script>
    import Clicker from "../components/clicker.svelte"
    //import Cats from "../components/cats.svelte"
    import ControlledCats from "../components/controlled-cats.svelte"
    let name = "Jeff"
</script>

<h1>Welcome {name}</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
<Clicker />
<ControlledCats />