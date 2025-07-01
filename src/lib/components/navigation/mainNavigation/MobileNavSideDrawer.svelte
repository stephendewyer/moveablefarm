<script lang="ts">
    import NavAccordion from "$lib/components/accordions/AccordionMobileNav.svelte"
    import MobileNavSideDrawerToggleButton from "$lib/components/navigation/mainNavigation/MobileNavSideDrawerToggleButton.svelte";
    import NavigationData from "$lib/data/navigationData.json";

    export let openMobileNav: boolean = false;

    let nav_data: NavTab[] = NavigationData;

</script>

<aside 
    class="{ (openMobileNav) ? 'side_drawer_open' : 'side_drawer_closed' }"
    aria-hidden="{ (openMobileNav) ? 'false' : 'true'}"
>
    <button
        class="sidedrawer_toggle_button"
        on:click={() => openMobileNav = !openMobileNav}
        on:keyup={() => openMobileNav = !openMobileNav}
    >
        <MobileNavSideDrawerToggleButton open={openMobileNav} />
    </button>
    <nav>
        <NavAccordion 
            mobileNavTabsData={nav_data}
            bind:openState={openMobileNav}
        />
    </nav>
</aside>

<style>
    aside {
        height: 100%;
        background: #EDF8F9;
        position: fixed;
        top: 0;
        left: 4rem;
        right: 0;
        z-index: 50;
    }

    .side_drawer_closed {
        transform: translateX(100%);
        transition: transform 0.3s ease-in-out;
    }

    .side_drawer_open {
        transform: translateX(0);
        transition: transform 0.3s ease-in-out;
    }

    .sidedrawer_toggle_button {
        padding: 1rem;
        background: none;
        border: none;
    }

    nav {
        width: 100%;
        padding: 2rem 2rem;
	}

    .logout_button_container {
        padding: 1rem 0;
    }
    
    @media (min-width: 1000px) {

        .side_drawer_closed {
            display: none;
        }

        .side_drawer_open {
            display: none;
        }
    }
</style>