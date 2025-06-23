<script lang="ts">
    import MoveableFarmLogo from "$lib/images/logo/moveable_farm_logo.svg?raw";
    import NavigationData from "$lib/data/navigationData.json";

    const leftMainNavData: NavTab[] = NavigationData.filter((navTab, index) => {
        return (
            index <= NavigationData.length/2
        ) && (
            navTab.name !== "index"
        );
    });

    console.log(leftMainNavData)

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
            <a href={navTab.route} >
                <li>
                    {navTab.name}
                </li>
            </a>
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
            <a href={navTab.route} >
                <li>
                    {navTab.name}
                </li>
            </a>
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
    }


    li {
        background-color: rgba(249, 238, 235, 0.5);
        transition: background-color 0.3s ease-out;
        padding: 1rem 2rem;
        color: #231F20;
    }

    li:hover {
        background-color: rgba(249, 238, 235, 0.75);
    }
</style>