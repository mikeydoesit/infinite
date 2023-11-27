<script>
    import { page } from '$app/stores';
</script>

<style>
    .tapBarMenu {
        @apply h-[11.5vh] bg-primary w-full fixed bottom-0 max-w-[576px] grid grid-cols-tapbarmenu grid-rows-tapbarmenu z-20 shadow-md;
    }
    .menuItem {
        @apply w-full flex justify-center items-center;
    }
    .active_wrapper {
        @apply rounded-full bg-white p-2;
    }
    img {
        @apply w-6 h-6;
    }
</style>

<div class="tapBarMenu">
    <a href="/" class="menuItem">
        {#if $page.url.pathname == '/'}
            <div class="active_wrapper">
                <img src="/images/home_active.png" alt="Home menu icon" />
            </div>
        {:else}
            <img src="/images/home.png" alt="Home menu icon" />
        {/if}
    </a>
    <a href="/search" class="menuItem">
        {#if $page.url.pathname.startsWith('/search')}
            <div class="active_wrapper">
                <img src="/images/search_active.png" alt="search icon" />
            </div>
        {:else}
            <img src="/images/search.png" alt="search icon" />
        {/if}
    </a>
    <a href="/classes" class="menuItem">
        {#if $page.url.pathname.startsWith('/classes')}
            <div class="active_wrapper">
                <img src="/images/classes_active.png" alt="calendar icon" />
            </div>
        {:else}
            <img src="/images/classes.png" alt="Newspaper icon" />
        {/if}
    </a>
    <a href="/events" class="menuItem">
        {#if $page.url.pathname.startsWith('/events')}
            <div class="active_wrapper">
                <img src="/images/event_active.png" alt="events icon" />
            </div>
        {:else}
            <img src="/images/event.png" alt="Home menu icon" />
        {/if}
    </a>
    <a href="/account" class="menuItem">
        {#if $page.url.pathname.startsWith('/account')}
            <div class="active_wrapper">
                <img src="/images/user_active.png" alt="User icon" />
            </div>
        {:else}
            <img src="/images/user.png" alt="User icon" />
        {/if}
    </a>
</div>