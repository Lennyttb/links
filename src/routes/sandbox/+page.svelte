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
            <h1 class="text-black font-medium font-serif text-5xl">Sandbox</h1>
            <p class="font-serif text-lg text-black text-opacity-60">
                A collection of design experimentations.
            </p>
        </div>
        <div class="flex flex-col gap-8 p-4 pb-32">
            {#each filteredCards as card (card.id)}
                <div
                    class="bg-[#f8f6f2] p-2 rounded-[1.25rem] border-1 shadow-sm"
                >
                    <div class="flex flex-row gap-2 p-2">
                        {#each card.tags as tag}
                            <span
                                class="py-1 px-2 bg-green-500 text-white rounded-[0.25rem] text-xs font-medium font-mono"
                                >{tag}</span
                            >
                        {/each}
                    </div>
                    <Card.Root
                        class="flex flex-col gap-4 rounded-[1rem] p-[0.75rem] bg-card border-0"
                    >
                        <Card.Content class="flex flex-col gap-2 p-0">
                            <div
                                href={card.pagelink}
                                class="rounded-[0.25rem] object-cover overflow-hidden w-full h-[400px]"
                            >
                                <img
                                    class="h-full w-full object-cover"
                                    src={card.image}
                                    alt=""
                                />
                            </div>
                        </Card.Content>
                    </Card.Root>
                </div>
            {/each}
        </div>
    </div>
</main>
