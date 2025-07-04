<script lang="ts">
    import FarmerSocialLogin from "../logins/FarmerSocialLogin.svelte";
    import FarmerSocialBanner from "$lib/images/cards/farmer.jpg";
</script>

<div class="card_container">
    <div class="farmer_social_banner">
        <img src={FarmerSocialBanner} alt="farmer" />
    </div>
    <div class="card_info">
        <h2>farmer social</h2>
        <p>Connect to a network of farmers in your area to share tips, resources and experiences.</p>
        <FarmerSocialLogin />
        <div class="secondary_actions">
            <div class="action_column">
                don't have an account?
            </div>
            <div class="action_column">
                forgot password?
            </div>
        </div>
    </div>

    

</div>

<style>

    .card_container {
        width: 100%;
        max-width: 40rem;
        background-color: #EBF4F9;
    }

    .farmer_social_banner {
        width: 100%;
    }

    .card_info {
        display: flex;
        flex-direction: column;
        gap: 1rem;
        color: #434041;
        padding: 1rem;
    }

    p {
        color: #434041;
    }

    .secondary_actions {
        display: flex;
        flex-direction: row;
        gap: 1rem;
    }

</style>