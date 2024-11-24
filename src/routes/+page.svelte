<script lang="ts">
    import * as Card from "$lib/components/ui/card";
    import Button from "$lib/components/ui/button/button.svelte";
    import * as Avatar from "$lib/components/ui/avatar";
    import cardData from "$lib/data/card.json";
    import type { Card as CardType } from "$lib/types/card.ts";
    const cards: CardType[] = cardData;
    import { marked } from "marked";
    import { page } from "$app/stores";
    import { derived } from "svelte/store";

    const currentPath = derived(page, ($page) => $page.url.pathname);

    let filteredCards: CardType[] = [];
    $: filteredCards = cardData.filter((card) => card.page === $currentPath);

    console.log(page);
</script>

<main class="flex flex-col items-center justify-center w-full">
    <div class="flex flex-col h-auto w-[560px]">
        <div class="flex flex-col p-4 mt-8 gap-4">
            <div
                class="flex flex-row justify-center items-center gap-2 w-fit py-1 px-2 rounded-full bg-black bg-opacity-5 border-0"
            >
                <div class=" size-2 rounded-full bg-green-500"></div>
                <div class="text-sm text-black text-opacity-80">
                    Open to Freelance
                </div>
            </div>
            <h1 class="text-black font-medium font-serif text-5xl">
                Lenny Attab
            </h1>
            <p class="font-serif text-lg text-black text-opacity-60">
                Design Engineer based in Copenhagen
            </p>
            <p class="font-sans text-lg text-black text-opacity-60">
                I work with businesses of all scale to create world-class
                products and websites. Crafting beautiful and intuitive
                interfaces for both mobile and desktops since 2020.
            </p>
            <div class="flex flex-row gap-2 items-center">
                <Button class="w-fit py-1 px-2 h-fit">Reach out</Button>
                <Button variant="outline" class="w-fit py-1 px-2 h-29"
                    >Resume</Button
                >
            </div>
        </div>
        <div class="flex flex-col gap-8 p-4 pb-32">
            {#each filteredCards as card (card.id)}
                <div
                    class="bg-[#f8f6f2] p-2 rounded-[1.25rem] border-1 shadow-sm"
                >
                    <Card.Root
                        class="flex flex-col gap-4 rounded-[1rem] p-[0.75rem] bg-card border-0"
                    >
                        <Card.Content class="flex flex-col gap-2 p-0">
                            <!--<div class="flex flex-row gap-2">
                                {#each card.tags as tag}
                                    <span
                                        class="py-1 px-2 bg-green-500 text-white rounded-[0.25rem] text-xs font-medium font-mono"
                                        >{tag}</span
                                    >
                                {/each}
                            </div>--->
                            <a
                                href={card.pagelink}
                                class="rounded-[0.25rem] object-cover overflow-hidden w-full h-[300px] hover:*:scale-105"
                            >
                                <img
                                    class="h-full w-full object-cover transition-transform"
                                    src={card.image}
                                    alt=""
                                />
                            </a>
                        </Card.Content>
                        <Card.Footer
                            class="flex flex-col gap-1 items-start justify-start p-0"
                        >
                            <article
                                class="prose-a:text-blue-600 hover:prose-a:text-blue-500 text-s mb-1"
                            >
                                {@html marked(card.description)}
                            </article>

                            <Button
                                variant="outline"
                                class="w-fit py-1 px-2 h-fit"
                                href={card.pagelink}
                                target="_blank">Visit {card.cta}</Button
                            >
                        </Card.Footer>
                    </Card.Root>
                </div>
            {/each}
        </div>
    </div>
</main>
