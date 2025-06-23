<script lang="ts">
    import "./styles.css";
    import MainNavigation from "$lib/components/navigation/mainNavigation/MainNavigation.svelte";
    import Footer from "$lib/components/navigation/footer/Footer.svelte";


    let footerElHeight: number = 0;
</script>

<div class="app">
    <MainNavigation />
	<main style="padding-bottom: {footerElHeight}px;">
		<slot />
	</main>
    <Footer bind:footerHeight={footerElHeight} />
</div>

<style>

	.app {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
		position: relative;
		overflow-x: hidden;
	}

	main {
		display: flex;
		flex-direction: column;
		width: 100%;
		margin: 0 auto;
	}

</style>