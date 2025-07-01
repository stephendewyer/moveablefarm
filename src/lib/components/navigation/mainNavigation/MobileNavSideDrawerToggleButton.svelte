<script lang="ts">
	export let open: boolean = false;
</script>

<button 
	class="hamburger" 
	class:open 
	on:click={() => open = !open}
	on:keyup={() => open = !open}
	aria-pressed={open}
	aria-label="open navigation sidedrawer"
>
    <svg width=32 height=24>
        <line id="top" x1=0 y1=2  x2=32 y2=2/>
        <line id="middle" x1=0 y1=12 x2=32 y2=12/>
        <line id="bottom" x1=0 y1=22 x2=32 y2=22/>
    </svg>
</button>

<style>

    button {
        position: relative;
	}

    .hamburger {
        cursor: pointer;
        border: none;
        outline: none;
        position: relative;
        background: none;
		padding: 1rem;
		margin: 0;
		background-color: rgba(249, 238, 235, 0.5);
        transition: background-color 0.3s ease-out;
    }

	.hamburger:hover {
		background-color: rgba(249, 238, 235, 0.75);
	}

	.hamburger:hover > svg > line {
		stroke: #145aa9;
	}

    .hamburger:focus {
        outline: none;
    }

	svg {
		min-height: 28px;
		transition: transform 0.3s ease-in-out;
	}
	
	svg line {
		stroke: #231F20;
		stroke-width: 3;
		transition: transform 0.3s ease-in-out, stroke 0.3s ease-in-out;
	}
	
	.open svg {
		transform: scale(1)
	}

	.open > svg line {
		stroke: #231F20;
	}

	.open:hover > svg line {
		stroke: #145aa9;
	}
	
	.open #top {
		transform: translate(6px, 0px) rotate(45deg)
	}
	
	.open #middle {
		opacity: 0;
	}
	
    .open #bottom {
		transform: translate(-12px, 9px) rotate(-45deg)
	}

</style>