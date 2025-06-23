<script lang="ts">
    import MoveableFarmLogo from "$lib/images/logo/moveable_farm_logo.svg?raw";
    const today = new Date();
    const year = today.getFullYear();
    export let footerHeight;
</script>
<footer bind:clientHeight={footerHeight}>
    <div class="logo">
        {@html MoveableFarmLogo}
    </div>
</footer>
<style>
    footer {
        position: absolute;
        bottom: 0;
        width: 100%;
    }
    .logo {
        width: 20rem;
    }
</style>