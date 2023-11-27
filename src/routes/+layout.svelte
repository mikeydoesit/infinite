<script>
    import "../styles/app.css";
    import Tapbar from "../lib/components/Tapbar.svelte";
	import Header from "../lib/components/Header.svelte";
	import { fade } from 'svelte/transition'
	import { onMount } from 'svelte';

    let showLoader

    const storage = window.sessionStorage.getItem('visitState') || '0'

	if (storage == '0') {
        showLoader = true
    } else if (storage == '1') {
        showLoader = false
    }

    onMount(() => {
        if(showLoader) {
            setTimeout(() => {
                window.sessionStorage.setItem('visitState', '1')
                showLoader = false
            }, 7500)
        }
    })
</script>

<style>
	/* main {
		@apply h-screen relative;
	} */
    .loaderWrapper {
        @apply bg-primary h-screen flex flex-col items-center justify-center py-32 px-10 transition-all duration-[1100ms] ease-out opacity-100 z-50 absolute w-full;
    }
    .loader_header {
        @apply text-white text-center w-full mt-4;
    }
    .header_title {
        @apply text-white font-extrabold text-4xl;
    }
    .homepage_content {
        @apply overflow-y-auto h-screen w-full;
    }
	.loader {
        @apply max-h-[300px];
        animation: pulse 2s linear infinite;
    }
    @keyframes pulse {
    0% { transform: scale(0.95); }
    50% { transform: scale(1); }
    100% { transform: scale(0.95); }
    }
</style>


{#if showLoader}
<div class="loaderWrapper" transition:fade>
    <img class="loader" src="/images/dkfc.png" alt="dkfc logo" />
    <div class="loader_header">
        <h1 class="header_title">Dansoman<br/>Keep Fit Club</h1>
    </div>
</div>
{/if}

<div class="homepage_content">
    <Header />
    <slot />
    <Tapbar />
</div>