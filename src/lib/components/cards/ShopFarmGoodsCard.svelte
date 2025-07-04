<script lang="ts">
    import CustomerLogin from "../logins/CustomerLogin.svelte";
    import videojs from "video.js";
    import "video.js/dist/video-js.min.css";
    import type Player from "video.js/dist/types/player";
    import { onDestroy, onMount } from "svelte";
    import ThreeDBasket from "$lib/videos/3D_basket_animation.mp4";
    import ThreeDBasketPoster from "$lib/videos/3D_animated_basket_still.jpg";

    let player: Player;

    onMount(() => {
        player = videojs("player", {fluid: true});
    });

    onDestroy(() => {
        if (player) {
            player.dispose();
        };
    });
</script>

<div class="card_container">
    <div class="banner_video">
        <video 
            class="video-js"
            controls 
            id="player"
            muted={true}
            autoplay={true}
            poster={ThreeDBasketPoster}
            loop={true}
        >
            <track kind="captions">
            <source src={ThreeDBasket} type="video/mp4"/>
        </video>
    </div>
    <div class="card_info">
        <h2>
            shop farm goods
        </h2>
        <p>
            Order farm goods directly from farmers.
        </p>
        <CustomerLogin /> 
    </div>

</div>

<style>

    
    .card_container {
        width: 100%;
        max-width: 40rem;
        background-color: #EBF4F9;
    }

    .banner_video {
        width: 100%;
    }

    .card_info {
        display: flex;
        flex-direction: column;
        gap: 1rem;
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