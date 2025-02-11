<script lang="ts">
    import { navStore } from "$lib/navStore";
    import AddData from "./AddData.svelte";
    import Home from "./Home.svelte";
    import global_constants from "$lib/global-constants";
    let navItem!: string;
    let drawerOpen = false;
    let i = 0;
    navStore.subscribe((res) => {
        navItem = res;
        if (res == "home") {
            if (drawerOpen) {
                setTimeout(() => {
                    drawerOpen = false;
                }, global_constants.styles.timing * 1000);
            }
        }
        if (res == "add-data") {
            i += 1;
            console.log(i);
            
            drawerOpen = true;
        }
    });
</script>

<div class="container main-container">
    <div class="home">
        <Home />
    </div>
    {#if drawerOpen}
        <div
            class={navItem == "add-data"
                ? "add_data open-drawer"
                : "add_data close-drawer"}
        >
            <AddData />
        </div>
    {/if}
</div>

<style>
    .container {
        height: 100%;
        position: relative;
        overflow: hidden;
    }
    .add_data {
        position: absolute;
        top: 0;
        box-shadow: 0 0 10px var(--theme);
        height: 100%;
        width: 20rem;
        right: 0;
        z-index: 1;
        border-radius: 1rem;
        background-color: var(--background-white);
    }
    .open-drawer {
        animation: open-drawer ease-in-out var(--timing);
    }
    .close-drawer {
        animation: close-drawer ease-in-out var(--timing);
    }
    @keyframes open-drawer {
        from {
            right: -20rem;
            box-shadow: 0 0 0px var(--theme);
        }
        to {
            right: 0;
            box-shadow: 0 0 10px var(--theme);
        }
    }
    @keyframes close-drawer {
        from {
            right: 0;
            box-shadow: 0 0 10px var(--theme);
        }
        to {
            right: -20rem;
            box-shadow: 0 0 0px var(--theme);
        }
    }
    .home {
        height: 100%;
        overflow: hidden;
        overflow-y: auto;
        scrollbar-gutter: stable;
    }
</style>
