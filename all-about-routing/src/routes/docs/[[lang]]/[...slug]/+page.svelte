<script>
    import {page} from '$app/stores';

    let slugArray=$page.params.slug.split('/')
</script>
<h1>
    The Routing Path is
    {#each slugArray as slug }
        {slug} /
    {/each}
</h1>
