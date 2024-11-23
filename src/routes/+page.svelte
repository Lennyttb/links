<script lang="ts">
    import * as Card from "$lib/components/ui/card";
    import Button from "$lib/components/ui/button/button.svelte";
    import cardData from "$lib/data/card.json";
    import type { Card as CardType } from "$lib/types/card.ts";
    const cards: CardType[] = cardData;
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
            {#each cards as card}
                <Card.Root
                    class="flex flex-col gap-0 rounded-[1rem] p-[0.75rem] shadow-sm bg-card"
                >
                    <Card.Content class="flex flex-col gap-2 p-0">
                        <div class="flex flex-row gap-2">
                            {#each card.tags as tag}
                                <span
                                    class="py-1 px-2 bg-black text-white rounded-[0.25rem] bg-opacity-30 text-xs font-medium font-mono"
                                    >{tag}</span
                                >
                            {/each}
                        </div>
                        <div
                            class="rounded-[0.25rem] object-cover overflow-hidden w-full h-[300px]"
                        >
                            <img
                                class="h-full w-full object-cover"
                                src={card.image}
                                alt=""
                            />
                        </div>
                    </Card.Content>
                    <Card.Footer class="p-4">
                        <p>{card.title}</p>
                    </Card.Footer>
                </Card.Root>
            {/each}
        </div>
    </div>
</main>
