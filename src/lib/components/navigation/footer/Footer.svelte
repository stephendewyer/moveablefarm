<script lang="ts">
    import MoveableFarmLogo from "$lib/images/logo/moveable_farm_logo.svg?raw";
    import BarleyBanner from "$lib/images/banners/barley_banner.jpg";
    import NavData from "$lib/data/navigationData.json";

    export let footerHeight;

    const today = new Date();
    const year = today.getFullYear();
    
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
                {#each NavData as navTab, index}
                    {#if navTab.name === "index"}
                        <a href={navTab.route}>
                            <li class="logo">
                                {@html MoveableFarmLogo}
                            </li>
                        </a>
                        
                    {/if}
                {/each}
                <div class="nav_tabs">
                    {#each NavData as navTab, index}
                        {#if navTab.name !== "index" && navTab.name !== "logins"}
                            {#if navTab.children.length === 0}
                                <li class="nav_tab">
                                    <a href={navTab.route}>
                                        {navTab.name}
                                    </a>
                                </li>
                            {:else if navTab.children.length > 0}
                                <div class="nav_column">
                                    <li class="nav_tab">
                                        <a href={navTab.route}>
                                            {navTab.name}
                                        </a>
                                    </li>
                                    {#each navTab.children as subNavTab, index}
                                        <li class="nav_tab">
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
                                    <a href={navTab.route}>
                                        {navTab.name}
                                    </a>
                                </li>
                                {#each navTab.children as subNavTab, index}
                                    <li class="nav_tab">
                                        <a href={subNavTab.route}>
                                            {subNavTab.name}
                                        </a>
                                    </li>
                                {/each}
                            </div>
                        {/if}
                    {/each}
                </div>
            </ul>
            <p>
                Moveable Farm © {year} | all rights reserved
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
    }

    .nav_column {
        display: flex;
        flex-direction: column;
        gap: 1rem;
    }

    .nav_tab {
        color: #231F20;
        font-size: 1rem;
        width: 12rem;
        font-weight: 600;
    }

    .nav_tab > a {
        color: #231F20;
        font-size: 1rem;
        width: 12rem;
        font-weight: 600;
    }

    .top {
        width: 100%;
        margin: 0;
        position: relative;
        height: 20rem;
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

    .bottom {
        background-color: #E6E1C2;
        height: 6rem;
    }

    .logo:hover {
        fill: #145aa9;
    }

    .logo {
        width: 16rem;
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
        align-items: center;
        justify-content: center;
    }

    .navigation {
        position: relative;
        padding: 1rem;
        display: flex;
        flex-direction: column;
        gap: 1rem;
    }

</style>