<script lang="ts">
    import logo from "$lib/media/logo.png"
    import '../app.css'
    import { page } from '$app/stores';
    import { ChessIcon, FlipHorizontalIcon, MarkerIcon, TimeOclockIcon, PhoneCallIcon, SearchIcon, MenuBurgerIcon } from 'svelte-uicons/rounded/regular'


    let isOpen = false
    function toggleBurgerMenu() {
        isOpen = !isOpen;
    }
</script>

<header class="bg-onyx p-4 z-50">
    <!-- Top Header w/ LOGO & Contact Info -->
    <div class="max-w-[1000px] mx-auto px-4 pb-2">
        <!-- Logo and Info -->
        <div class="flex flex-col md:flex-row md:items-center md:justify-between pb-6">
            <a href="/" class="mb-4 md:mb-0 mx-auto md:mx-0">
                <img src={logo} alt="">
            </a>
            
            <!-- Contact info -->
            <div class="flex flex-col items-center md:gap-10 gap-4 md:text-center md:flex-row">
                <div class="flex gap-2 items-center text-pumpkin">
                    <MarkerIcon size="13" />
                    <p class="text-seasalt text-xs">Strømparken 1, 8500 Grenaa</p>
                </div>

                <div class="flex gap-2 items-center text-pumpkin">
                    <TimeOclockIcon size="13" />
                    <span class="text-seasalt text-xs">Man - Søn 9.00 - 18.00</span>
                </div>

                <div class="flex gap-2 items-center text-pumpkin">
                    <a href="tel:+4586454578">
                        <PhoneCallIcon size="13" />
                    </a>
                    <span class="text-seasalt text-xs">[45] 86 45 45 78</span>
                </div>
            </div>
        </div>

        <!-- Navigation Bar -->
        <div class="bg-seasalt shadow-[0_35px_60px_-15px_rgba(255,255,255,0.5)] dr z-50 absolute left-0 text-md py-4 px-8 w-full max-w-screen-lg rounded-md md:absolute md:left-1/2 md:top-[85px] md:-translate-x-1/2 md:text-[13.5px] lg:text-[16px]">
            <nav class="md:flex md:justify-between md:flex-row-reverse md:items-center gap-6 relative z-50">
                
                <!-- Navigation Links -->
                <div class="flex items-center justify-between">

                    <button on:click={toggleBurgerMenu} class="flex md:hidden">
                        <MenuBurgerIcon size="16"/>
                    </button>
                    
                    <div class="relative">
                    <input class="rounded-md w-full md:w-auto p-1 md:p-2" type="text" placeholder="Søg">
                    <SearchIcon class="absolute top-[10px] md:top-[15px] right-4 stroke-1" size="14"/>
                </div>
                </div>
                 
                {#if isOpen}
                <ul class="flex flex-col md:flex-row gap-4 md:gap-10 uppercase font-medium p-4 rounded-lg w-max">
                        
                    <li><a class={$page.url.pathname === '/' ? 'text-pumpkin' : 'hover:text-pumpkin'} href="/">Forside</a></li>
                    <li><a class={$page.url.pathname === '/about' ? 'text-pumpkin' : 'hover:text-pumpkin'} href="/about">Om os</a></li>
                    <li><a class={$page.url.pathname === '/service' ? 'text-pumpkin' : 'hover:text-pumpkin'} href="/service">Service</a></li>
                    <li><a class={$page.url.pathname === '/faq' ? 'text-pumpkin' : 'hover:text-pumpkin'} href="/faq">Faq</a></li>
                    <li><a class={$page.url.pathname === '/nyheder' ? 'text-pumpkin' : 'hover:text-pumpkin'} href="/nyheder">Nyheder</a></li>
                    <li><a class={$page.url.pathname === '/kontakt' ? 'text-pumpkin' : 'hover:text-pumpkin'} href="/kontakt">Kontakt os</a></li>
                </ul>
                {:else if !isOpen}
                <ul class="hidden flex-col md:flex-row gap-4 md:gap-10 uppercase font-medium md:flex">
                    <li><a class={$page.url.pathname === '/' ? 'text-pumpkin' : ''} href="/">Forside</a></li>
                    <li><a class={$page.url.pathname === '/about' ? 'text-pumpkin' : ''} href="/about">Om os</a></li>
                    <li><a class={$page.url.pathname === '/service' ? 'text-pumpkin' : ''} href="/service">Service</a></li>
                    <li><a class={$page.url.pathname === '/faq' ? 'text-pumpkin' : ''} href="/faq">Faq</a></li>
                    <li><a class={$page.url.pathname === '/nyheder' ? 'text-pumpkin' : ''} href="/nyheder">Nyheder</a></li>
                    <li><a class={$page.url.pathname === '/kontakt' ? 'text-pumpkin' : ''} href="/kontakt">Kontakt os</a></li>
                </ul>
                {/if}
            
            </nav>
        </div>
    </div>
</header>
