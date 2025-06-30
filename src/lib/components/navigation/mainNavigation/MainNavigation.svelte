<script lang="ts">
    import MainNavColumnDropdown from "./MainNavColumnDropdown.svelte";
    import MoveableFarmLogo from "$lib/images/logo/moveable_farm_logo.svg?raw";
    import NavigationData from "$lib/data/navigationData.json";

    const leftMainNavData: NavTab[] = NavigationData.filter((navTab, index) => {
        return (
            index <= NavigationData.length/2
        ) && (
            navTab.name !== "index"
        );
    });

    const rightMainNavData: NavTab[] = NavigationData.filter((navTab, index) => {
        return (
            index > NavigationData.length/2
        ) && (
            navTab.name !== "index"
        );
    });

    let indexTab: NavTab | null= null;

    NavigationData.forEach((navTab, index) => {
        if (navTab.name === "index") {
            indexTab = navTab;
        };
    });

</script>
<nav>
    <ul class="nav_tabs_desktop">
        {#each leftMainNavData as navTab, index}
            {#if navTab.children.length === 0}
                <a href={navTab.route} class="nav_column" >
                    <li>
                        {navTab.name}
                    </li>
                </a>
            {:else if navTab.children.length > 0}
                <MainNavColumnDropdown dropdownNavData={navTab} />
            {/if}
        {/each}
    </ul>
    {#if indexTab}
        <ul>
            <a href={indexTab?.route}>
                <li>
                    <div class="logo">
                        {@html MoveableFarmLogo}
                    </div>
                </li>
            </a>
        </ul>
    {/if}
    <ul class="nav_tabs_desktop">
        {#each rightMainNavData as navTab, index}
            {#if navTab.children.length === 0}
                <a href={navTab.route} class="nav_column">
                    <li>
                        {navTab.name}
                    </li>
                </a>
            {:else if navTab.children.length > 0}
                <MainNavColumnDropdown dropdownNavData={navTab} />
            {/if}
        {/each}
    </ul>
</nav>
<style>

    nav {
        display: flex;
        width: 100%;
        justify-content: center;
    }

    ul {
        list-style: none;
        padding: 0;
        margin: 0;
        display: flex;
    }

    .nav_tabs_desktop {
        width: 50%;
        display: flex;
        justify-content: center;
    }
    
    .logo {
        width: 20rem;
        fill: #231F20;
        transition: fill 0.3s ease-out;
    }

    .logo:hover {
        fill: #145aa9;
    }

    li {
        background-color: rgba(249, 238, 235, 0.5);
        transition: background-color 0.3s ease-out;
        padding: 1rem 2rem;
        color: #231F20;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        gap: 1rem;
        transition: color 0.3s ease-out, background-color 0.3s ease-out;
    }

    li:hover {
        background-color: rgba(249, 238, 235, 0.75);
        color: #145aa9;
    }

    .nav_column {
        display: flex;
        flex-direction: column;
        width: 100%;
        max-width: 14rem;
    }

    @media screen and (max-width: 1440px) {
        .logo {
            max-width: 14rem;
        }

        .nav_column {
            width: 10rem;
        }
    }

    @media screen and (max-width: 1080px) {
        .logo {
            max-width: 10rem;
        }

        .nav_column {
            width: 8rem;
        }
    }

    @media screen and (max-width: 720px) {
        .logo {
            max-width: 8rem;
        }
    }

</style>