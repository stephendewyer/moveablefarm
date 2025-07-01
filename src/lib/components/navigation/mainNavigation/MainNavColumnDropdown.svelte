<script lang="ts">
    import Arrow from "$lib/images/icons/arrow.svg?raw";
    import LoginIcon from "$lib/images/icons/login_icon.svg?raw";

    export let dropdownNavData: NavTab;

    let openDropdown: boolean = false;

    let navDropdownHeight: number = 0;

</script>
<div 
    class="nav_column"
    on:mouseenter={() => openDropdown = true}
    on:mouseleave={() => openDropdown = false}
    on:keyup={() => openDropdown = true}
    tabindex={dropdownNavData.index}
    role="tab"
>
    <li class="nav_dropdown_toggle_tab">

        <a href={dropdownNavData.route}>
                {#if dropdownNavData.name === "logins"}
                    <div class="login_icon">
                        {@html LoginIcon}
                    </div>
                {/if}
                {dropdownNavData.name}
        </a>
        <div id="toggle_arrow" class={openDropdown ? "toggle_arrow_active": "toggle_arrow_inactive"}>
            {@html Arrow}
        </div>
    </li>
    <div 
        id="nav_dropdown_menu_container"
        role="tabpanel"
    >
        <div 
            id="nav_dropdown_menu"
            style={openDropdown ? `height: ${navDropdownHeight}px;` : `height: 0px;`}
        >
            <ul 
                bind:clientHeight={navDropdownHeight}
                id="nav_dropdown_menu_inner"
            >
                {#each dropdownNavData.children as subNavTab, index}
                    <a href={subNavTab.route}>
                        <li>
                            <div 
                                id="dropdown_tab"             
                                style={openDropdown ? `opacity: ${100}%;` : `opacity: 0;`}
                            >
                                {subNavTab.name}
                            </div>
                        </li>
                    </a>
                {/each}
            </ul>
        </div>
    </div>
</div>

<style>

    .nav_column {
        display: flex;
        flex-direction: column;
        width: 100%;
        max-width: 14rem;
        position: relative;
    }

    .nav_dropdown_toggle_tab {
        display: flex;
        position: relative;
    }

    #nav_dropdown_menu_container {
        position: relative;
    }

    #nav_dropdown_menu {
        width: 100%;
        position: relative;
        overflow: hidden;
        will-change: height;
        transition: height 0.4s cubic-bezier(0.65, 0.05, 0.36, 1);
    }

    #nav_dropdown_menu_inner {
        list-style: none;
        position: relative;
        height: auto;
        transition: opacity 0.3s linear 0.18s;
        padding: 0;
    }

    #toggle_arrow {
        fill: #231F20;
        width: 0.5rem;
        will-change: transform;
        transition: transform 0.2s ease-out;
    }

    .toggle_arrow_inactive {
        transform: rotateX(0) rotate(90deg);
    }

    .toggle_arrow_active {
        transform: rotateX(180deg) rotate(90deg);
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
    }

    li > a {
        color: #231F20;
        display: flex;
        flex-direction: row;
        gap: 0.5rem;
        transition: color 0.3s ease-out;
    }

    li > a:hover {
        color: #145aa9;
    }

    li > a:hover > .login_icon {
        fill: #145aa9;
    }

    .login_icon {
        width: 1rem;
        transition: fill 0.3s ease-out;
    }

    #dropdown_tab {
        will-change: opacity;
        transition: opacity 0.4s ease-out;
        color: #231F20;
        transition: color 0.3s ease-out;
    }

    a:hover > li > #dropdown_tab {
        color: #145aa9;
    }


    li:hover {
        background-color: rgba(249, 238, 235, 0.75);
    }    

    @media screen and (max-width: 1440px) {

        .nav_column {
            width: 10rem;
        }
    }

    @media screen and (max-width: 1080px) {

        .nav_column {
            width: 8rem;
        }
    }

    @media screen and (max-width: 720px) {

    }
</style>