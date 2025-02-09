<script>
    import TopNavigation from "./../components/TopNavigation.svelte";
    import "../index.css";
</script>

<div class="page">
    <div class="top_nav">
        <TopNavigation />
    </div>
    <div class="body">
        <slot />
    </div>
</div>

<style>
    .page {
        height: 100vh;
        overflow: auto;
        position: relative;
        background-color: var(--theme);
    }
    .top_nav {
        height: 4rem;
        width: 100%;
        position: sticky;
        padding: 8px;
    }
    .body {
        height: calc(100% - ( 4rem + 8px ));
        margin: 0 8px;
        border: 2px solid var(--theme);
        border-radius: 1rem;
        padding: 1rem;
        background-color: white;
    }
</style>
