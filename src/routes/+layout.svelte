<script lang="ts">
    import "../app.css";
    import { page } from "$app/stores";
    import { get } from "svelte/store";

    const url = get(page).url;

    const pages = [
        { id: 0, name: "Home", route: "/" },
        //{ id: 1, name: "Services", route: "/services" },
        { id: 2, name: "Sandbox", route: "/sandbox" },
        //{ id: 3, name: "Writings", route: "/writings" },
        //{ id: 4, name: "Stack", route: "/stack" },
    ];
    console.log(pages[0]);
    console.log(pages[1]);
</script>

<main class="flex flex-col justify-start items-center h-auto">
    <nav class="flex fixed z-50 bottom-10 w-full items-center justify-center">
        <ul class="flex flex-row rounded-[0.75rem] p-[0.25rem] bg-black gap-4">
            <div class="flex flex-row gap-0">
                {#each pages as { id, name, route } (id)}
                    <li
                        class="flex justify-center items-center w-[90px] py-1 px-2 rounded-[0.5rem] {$page
                            .url.pathname === route
                            ? 'bg-gray-200'
                            : 'bg-black'}"
                    >
                        <a
                            href={route}
                            class="p-0 m-0 font-medium {$page.url.pathname ===
                            route
                                ? 'text-black'
                                : 'text-white'}"
                        >
                            {name}
                        </a>
                    </li>
                {/each}
            </div>
        </ul>
    </nav>

    <slot class="max-w-[500px]"></slot>
</main>
