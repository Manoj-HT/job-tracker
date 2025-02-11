<script lang="ts">
    import global_constants from "$lib/global-constants";
    import { navStore } from "$lib/navStore";

    let navItems = [
        {
            title: "Home",
            route: "home",
        },
        {
            title: "Add data",
            route: "add-data",
        },
    ];
    let appNames = ["NAUKRI", "APNA"];
    let app = appNames[0];
    let drawerState = {
        element: false,
        animaton: false,
    };
    function onclick(route: string) {
        navStore.set(route);
    }
    function appDrawer(
        e:
            | KeyboardEvent
            | (MouseEvent & {
                  currentTarget: EventTarget & HTMLDivElement;
              }),
    ) {
        if (drawerState.element) {
            drawerState.animaton = false;
            setApp(e as MouseEvent)
            setTimeout(() => {
                drawerState.element = false;
            }, global_constants.styles.timing * 1000);
        } else {
            drawerState = {
                element: true,
                animaton: true,
            };
        }
    }
    function setApp(e: MouseEvent){
        if((e.target as HTMLLIElement).localName != "li"){
            return;
        }
        app = (e.target as HTMLLIElement).innerText
    }
</script>

<div class="container">
    <div
        class="title"
        role="button"
        tabindex="0"
        onclick={(e) => appDrawer(e)}
        onkeydown={(e) => appDrawer(e)}
    >
        <span class="nav_item-box"></span>
        JOB TRACKER : &nbsp;&nbsp; <b>{app}</b>
        {#if drawerState.element}
            <div
                class={drawerState.animaton
                    ? "app_list open-drawer"
                    : "app_list close-drawer"}
            >
                <ul class="app_list_" >
                    {#each appNames as appName}
                        <li>
                            {appName}
                        </li>
                    {/each}
                </ul>
            </div>
        {/if}
    </div>
    <ul class="nav">
        {#each navItems as nav}
            <button
                class="nav_item transparency"
                onclick={() => {
                    onclick(nav.route);
                }}
            >
                <span class="nav_item-box"></span>
                {nav.title}
            </button>
        {/each}
    </ul>
</div>

<style>
    .container {
        width: 100%;
        height: 100%;
        border: 2px solid var(--theme);
        border-radius: 1rem;
        background-color: var(--background-white);
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 1rem;
    }
    .title {
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;
        height: 100%;
    }
    .title > .nav_item-box{
        cursor: pointer;
    }
    .nav {
        list-style: none;
        display: flex;
        gap: 10px;
        height: 100%;
    }
    .nav_item {
        width: 100px;
        display: flex;
        justify-content: center;
        align-items: center;
        cursor: pointer;
        position: relative;
    }
    .nav_item-box {
        position: absolute;
        border-bottom: 0px solid var(--theme);
        transition-duration: var(--timing);
        width: 100%;
        height: 100%;
    }
    .nav_item-box:hover {
        border-width: 5px;
    }
    .nav_item-box:active {
        width: 50%;
    }
    .app_list {
        position: absolute;
        top: calc(100% + 10px);
        padding: 1rem;
        height: calc(100vh - (4rem + 8px));
        width: 15rem;
        left: -1rem;
        background-color: var(--background-white);
        border-radius: 1rem;
        box-shadow: 0 0 10px var(--theme);
    }
    .open-drawer {
        animation: open_drawer ease-in-out var(--timing);
    }
    @keyframes open_drawer {
        from {
            left: -16rem;
        }
        to {
            left: -1rem;
        }
    }
    .close-drawer {
        animation: close_drawer ease-in-out var(--timing);
    }
    @keyframes close_drawer {
        from {
            left: -1rem;
        }
        to {
            left: -16rem;
        }
    }
    .app_list_{
        list-style: none;
    }
    .app_list_ > li {
        padding: 5px 1rem;
        cursor: pointer;
        transition-duration: var(--timing);
        border-left: 8px solid transparent;
        margin-bottom: 10px;
    }
    .app_list_ > li:hover {
        border-left: 8px solid var(--theme);
    }
</style>
