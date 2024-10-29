<script lang="ts">
    export let data;
    const { article } = data;

    let completePath = "http://localhost:5333/images/news/"
</script>

{#if article}
    <article class="mt-40">
        <div class="border-b-2 rounded-xl w-[300px] md:w-[600px] mx-auto shadow-xl">
            <img class="w-full rounded-t-xl mb-10" src={completePath + article.image} alt="">
            <h1 class="text-xl md:text-4xl text-center mb-10">{article.title} <span class="italic text-xs">{new Date(article.received).toLocaleDateString()}</span></h1>
            <div class="px-6 md:px-20 py-2 text-xs md:text-lg leading-6 mb-10">
                {@html article.content}
            </div>

        </div>
    </article>
{:else}
    <div>
        <h1>Ingen artikel blev fundet.</h1>
    </div>
{/if}

