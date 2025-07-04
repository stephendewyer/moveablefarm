<script lang="ts">
  import FarmerSocialCard from "$lib/components/cards/FarmerSocialCard.svelte";
  import ShopFarmGoodsCard from "$lib/components/cards/ShopFarmGoodsCard.svelte";
    import OrganicFarm from "$lib/images/banners/organic_farm.jpg"
</script>

<div>
    <div class="banner_container">
        <img class="banner" src={OrganicFarm} alt="organic farm"/>
        <div class="banner_gradient"></div>
        <div class="action_cards">
            <ShopFarmGoodsCard />
            <FarmerSocialCard />
        </div>
        
    </div>

</div>

<style>

    .banner_container {
        height: 100vh;
        width: 100%;
        object-fit: cover;
        position: relative;
    }

    .banner {
        width: 100%;
        height: 100%;
    }

    .banner_gradient {
        top: 0;
        bottom: 0;
        right: 0;
        left: 0;
        position: absolute;
        background: #434041;
        background: linear-gradient(0deg,rgba(67, 64, 65, 1) 0%, rgba(67, 64, 65, 0.5) 15%, rgba(67, 64, 65, 0) 25%, rgba(67, 64, 65, 0) 100%);
    }

    .action_cards {
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        display: flex;
        flex-direction: row;
        justify-content: space-around;
        align-items: center;
        gap: 1rem;
        padding: 0 1rem;
        max-width: 120rem;
        margin: 0 auto;
    }

</style>