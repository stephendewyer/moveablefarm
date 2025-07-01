<script lang="ts">
    import MainNavColumnDropdown from "./MainNavColumnDropdown.svelte";
    import MoveableFarmLogo from "$lib/images/logo/moveable_farm_logo.svg?raw";
    import NavigationData from "$lib/data/navigationData.json";
    import MobileNavSideDrawerToggleButton from "./MobileNavSideDrawerToggleButton.svelte";

    export let sideDrawer: boolean = false;

    let prevScrollPos: number = 0;

    let showNav: boolean = true; // boolean to show or hid nav bar

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

<svelte:window on:scroll={()=>{

    const handleScroll  = () => {
        // find current scroll position
        const currentScrollPos = window.scrollY || document.documentElement.scrollTop;

        // set state based on location info
        showNav = ((prevScrollPos > currentScrollPos) || currentScrollPos < 10);
        // set state to new scroll position
        prevScrollPos = currentScrollPos;
    };

    handleScroll();

}} />

<nav class={showNav ? "nav_bar_visible" : "nav_bar_hidden"}>
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
    <div id="nav_mobile">
        <MobileNavSideDrawerToggleButton bind:open={sideDrawer}/>
    </div>
</nav>
<style>
    .nav_bar_visible {
        top: 0;
        overflow: visible;
        position: fixed;
        left: 0;
        right: 0;
        height: 0;
        z-index: 3;
        display: flex;
        flex-direction: row;
        justify-content: center;
        will-change: top;
        transition: top 0.6s;
    }

    .nav_bar_hidden {
        top: -12rem;
        overflow: visible;
        position: fixed;
        left: 0;
        right: 0;
        height: 0;
        z-index: 3;
        display: flex;
        flex-direction: row;
        justify-content: center;
        will-change: top;
        transition: top 0.6s;
    }

    ul {
        list-style: none;
        padding: 0;
        margin: 0;
        display: flex;
        position: relative;
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

    #nav_mobile {
        display: none;
        margin: 0;
        position: relative;
    }

    .mobile_nav_menu_toggle_button_container {
        position: relative;
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

        .nav_bar_visible {
            justify-content: space-between;
        }

        .nav_bar_hidden {
            justify-content: space-between;
        }

        .logo {
            max-width: 8rem;
        }

        .nav_tabs_desktop {
            display: none;
        }

        #nav_mobile { 
            display: block;
        }
    }

</style>