<script lang="ts">
    import MoveableFarmLogo from "$lib/images/logo/moveable_farm_logo.svg?raw";
    import BarleyBanner from "$lib/images/banners/barley_banner.jpg";
    import NavData from "$lib/data/navigationData.json";

    export let footerHeight;

    const today = new Date();
    const year = today.getFullYear();

    
    const leftMainNavData: NavTab[] = NavData.filter((navTab, index) => {
        return (
            index <= NavData.length/2
        ) && (
            navTab.name !== "index"
        );
    });

    const rightMainNavData: NavTab[] = NavData.filter((navTab, index) => {
        return (
            index > NavData.length/2
        ) && (
            navTab.name !== "index"
        );
    });

    let indexTab: NavTab | null= null;

    NavData.forEach((navTab, index) => {
        if (navTab.name === "index") {
            indexTab = navTab;
        };
    });
    
</script>
<footer bind:clientHeight={footerHeight}>
    <div class="top">
        <img src={BarleyBanner} alt="barley banner" />
        <div class="barley_gradient"></div>
    </div>
    <div class="bottom">
        
    </div>
    <div class="navigation_container">
        <div class="navigation">
            <ul class="navigation_top">
                <a href={indexTab?.route}>
                    <li class="logo">
                        {@html MoveableFarmLogo}
                    </li>
                </a>
                <div class="nav_tabs">
                    <div class="nav_tabs_left">
                        {#each leftMainNavData as navTab, index}
                            {#if navTab.name !== "index" && navTab.name !== "logins"}
                                {#if navTab.children.length === 0}
                                    <li class="nav_tab">
                                        <a href={navTab.route}>
                                            {navTab.name}
                                        </a>
                                    </li>
                                {:else if navTab.children.length > 0}
                                    <div class="nav_column">
                                        <li class="nav_tab" >
                                            <a href={navTab.route} class="nav_tab_parent">
                                                {navTab.name}
                                            </a>
                                        </li>
                                        {#each navTab.children as subNavTab, index}
                                            <li class="nav_tab_child">
                                                <a href={subNavTab.route}>
                                                    {subNavTab.name}
                                                </a>
                                            </li>
                                        {/each}
                                    </div>
                                {/if}
                            {:else if navTab.name === "logins"}
                                <div class="nav_column">
                                    <li class="nav_tab">
                                        <a href={navTab.route} class="nav_tab_parent">
                                            {navTab.name}
                                        </a>
                                    </li>
                                    {#each navTab.children as subNavTab, index}
                                        <li class="nav_tab_child">
                                            <a href={subNavTab.route}>
                                                {subNavTab.name}
                                            </a>
                                        </li>
                                    {/each}
                                </div>
                            {/if}
                        {/each}
                    </div>
                    <div class="nav_tabs_right">
                        {#each rightMainNavData as navTab, index}
                            {#if navTab.name !== "index" && navTab.name !== "logins"}
                                {#if navTab.children.length === 0}
                                    <li class="nav_tab">
                                        <a href={navTab.route}>
                                            {navTab.name}
                                        </a>
                                    </li>
                                {:else if navTab.children.length > 0}
                                    <div class="nav_column">
                                        <li class="nav_tab" >
                                            <a href={navTab.route} class="nav_tab_parent">
                                                {navTab.name}
                                            </a>
                                        </li>
                                        {#each navTab.children as subNavTab, index}
                                            <li class="nav_tab_child">
                                                <a href={subNavTab.route}>
                                                    {subNavTab.name}
                                                </a>
                                            </li>
                                        {/each}
                                    </div>
                                {/if}
                            {:else if navTab.name === "logins"}
                                <div class="nav_column">
                                    <li class="nav_tab">
                                        <a href={navTab.route} class="nav_tab_parent">
                                            {navTab.name}
                                        </a>
                                    </li>
                                    {#each navTab.children as subNavTab, index}
                                        <li class="nav_tab_child">
                                            <a href={subNavTab.route}>
                                                {subNavTab.name}
                                            </a>
                                        </li>
                                    {/each}
                                </div>
                            {/if}
                        {/each}
                    </div>
                </div>
            </ul>
            <p class="copyright">
                Created by <a href="https://artintechservices.com" target="_blank" class="external_link">Art in Tech Services</a> | Art in Tech Services © {year} | All rights reserved
            </p>
        </div>
        
    </div>
</footer>
<style>
    footer {
        position: absolute;
        bottom: 0;
        width: 100%;
    }

    p {
        color: #231F20;
        margin: 0;
        padding: 0;
    }

    .navigation_top {
        display: flex;
        flex-direction: row;
    }

    ul {
        list-style: none;
        padding: 0;
        margin: 0;
        display: flex;
        gap: 2rem;
    }

    .nav_tabs {
        display: flex;
        gap: 1rem;
        flex-direction: row;
    }

    .nav_tabs_left {
        display: flex;
        gap: 1rem;
        flex-direction: row;
    }

    .nav_tabs_right {
        display: flex;
        gap: 1rem;
        flex-direction: row;
    }

    .nav_column {
        display: flex;
        flex-direction: column;
        gap: 1rem;
    }

    .nav_tab {
        color: #231F20;
        font-size: 1rem;
        width: 10rem;
        font-weight: 600;
    }

    .nav_tab > a {
        color: #231F20;
        font-size: 1rem;
        font-weight: 600;
        transition: color 0.3s ease-out;
    }

    .external_link {
        color: #231F20;
        transition: color 0.3s ease-out;
    }

    .external_link:hover {
        color: #145aa9;
    }

    .nav_tab_child > a {
        color: #231F20;
        font-size: 0.9rem;
        font-weight: 600;
        transition: color 0.3s ease-out;
    }

    a:hover {
        color: #145aa9;
    }

    .top {
        width: 100%;
        margin: 0;
        position: relative;
        height: 20rem;
    }

    .bottom {
        background-color: #E6E1C2;
        height: 6rem;
    }

    .top > img {
        object-fit: cover;
        width: 100%;
        height: 100%;
    }

    .barley_gradient {
        top: 0;
        bottom: 0;
        right: 0;
        left: 0;
        position: absolute;
        background: #E6E1C2;
        background: linear-gradient(0deg,rgba(230, 225, 194, 1) 0%, rgba(230, 225, 194, 1) 25%, rgba(230, 225, 194, 0) 100%);
    }

    .logo:hover {
        fill: #145aa9;
    }

    .logo {
        width: 14rem;
        fill: #231F20;
        transition: fill 0.3s ease-out;
    }

    .navigation_container {
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }

    .navigation {
        position: relative;
        padding: 1rem;
        display: flex;
        flex-direction: column;
        gap: 2rem;
    }

    .nav_tab_parent {
        text-decoration: underline;
    }

    .copyright {
        text-align: center;
        font-size: 0.9rem;
    }

    @media screen and (max-width: 1440px) {

        .navigation_top {
            flex-direction: column;
            align-items: center;
        }
    }

    @media screen and (max-width: 1080px) {

        .logo {
            width: 10rem;
        }

        .top {
            height: 18rem;
        }

        .bottom {
            height: 18rem;
        }

        .navigation_top {
            flex-direction: column;
            align-items: center;
        }

        .navigation {
            width: 100%;
        }

        .nav_tabs {
            width: 100%;
        }

        .nav_tabs_left {
            flex-direction: column;
            align-items: center;
            width: 100%;
        }

        .nav_tabs_right {
            flex-direction: column;
            align-items: center;
            width: 100%;
        }

        .nav_tab_child {
            padding: 0 0 0 1rem;
        }
    }

    @media screen and (max-width: 720px) {
        .logo {
            width: 8rem;
        }
    }

</style>