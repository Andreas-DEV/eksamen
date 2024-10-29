<script lang="ts">
    import { onMount } from "svelte";

    import {
        AirConditionerIcon,
        PowerIcon,
        CameraIcon,
        HeatIcon,
    } from "svelte-uicons/rounded/regular";

    import womanWorker from '$lib/media/about/1.png'

    let servicesData = [];
    let isLoading = true;
    let error = null;

    let completePath = "http://localhost:5333/images/service/";

    onMount(async () => {
        try {
            const response = await fetch("http://127.0.0.1:5333/service");
            if (!response.ok) {
                throw new Error("Kunne ikke finde data.");
            }
            servicesData = await response.json();
        } catch (err) {
            error = err.message;
            console.error("Error:", err);
        } finally {
            isLoading = false;
        }
    });
</script>

<section class="px-10 mx-auto py-28 max-w-screen-2xl">
    <h2 class="text-4xl sm:text-5xl font-semibold">
        Vores <span class="text-pumpkin">Services</span>
    </h2>
    <p class="my-4 px-1 text-dimGray text-xl">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Pariatur,
        nesciunt accusantium. Libero.
    </p>

    <div class="flex items-center mb-20">
        <div class="border-2 rounded-full w-3 h-3 border-pumpkin mx-1"></div>
        <span class="pb-[20px] text-platinum font-semibold text-xl select-none"
            >____________</span
        >
    </div>

    {#if servicesData && servicesData.length > 0}
    <div class="flex flex-col lg:flex-row gap-14 ">
        <div class="py-8 lg:py-14 flex flex-col">
            <div class="flex flex-col lg:flex-row gap-8 lg:gap-14">
                <div class="flex gap-6">
                    <PowerIcon class="text-pumpkin" size="64" />
                    <div>
                        <h2 class="text-xl font-semibold">
                            {servicesData[2].title}
                        </h2>
                        <p class="max-w-[35ch] my-4 text-dimGray">
                            {servicesData[2].teaser}
                        </p>
                    </div>
                </div>
                <div class="flex gap-6">
                    <CameraIcon class="text-pumpkin" size="64" />
                    <div>
                        <h2 class="text-xl font-semibold">
                            {servicesData[1].title}
                        </h2>
                        <p class="max-w-[35ch] my-4 text-dimGray">
                            {servicesData[1].teaser}
                        </p>
                    </div>
                </div>
            </div>
    
            <div class="flex flex-col lg:flex-row gap-8 lg:gap-14">
                <div class="flex gap-6">
                    <AirConditionerIcon class="text-pumpkin" size="64" />
                    <div>
                        <h2 class="text-xl font-semibold">
                            {servicesData[2].title}
                        </h2>
                        <p class="max-w-[35ch] my-4 text-dimGray">
                            {servicesData[2].teaser}
                        </p>
                    </div>
                </div>
                <div class="flex gap-6">
                    <HeatIcon class="text-pumpkin" size="64" />
                    <div>
                        <h2 class="text-xl font-semibold">
                            {servicesData[2].title}
                        </h2>
                        <p class="max-w-[35ch] my-4 text-dimGray">
                            {servicesData[2].teaser}
                        </p>
                    </div>
                </div>
            </div>
        </div>
        <img 
            src={womanWorker} 
            alt="" 
            class="w-[200px] sm:w-[400px] md:w-[400px] lg:w-[500px] xl:w-[500px] mx-auto object-contain"
        >
    </div>
    {/if}

    <section>

    </section>
</section>
