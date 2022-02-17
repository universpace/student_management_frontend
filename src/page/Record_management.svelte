<script>
    import {Styles} from "sveltestrap";
    import {location, link} from "svelte-spa-router"
</script>
<Styles/>
<style>
    .recordmain{
        height: 100%;
        padding: 0;
        margin: 0;
        width: 100%;
        background-color:red;
    }
</style>
<main class="recordmain">
    <p>{$location}</p>
</main>
