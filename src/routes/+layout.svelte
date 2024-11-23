<script lang="ts">
    import "../app.css";
</script>

<main
    class="flex flex-col justify-start items-center h-auto bg-gradient-to-t from-[#f8f6f2] to-[#f4f0e6]"
>
    <nav class="flex fixed bottom-10 w-full items-center justify-center">
        <ul class="flex flex-row rounded-[0.75rem] p-[0.25rem] bg-black gap-4">
            <div class="flex flex-row gap-0">
                <li
                    class="flex justify-center items-center w-[90px] py-1 px-2 bg-gray-200 rounded-[0.5rem]"
                >
                    <a href="" class="p-0 m-0 text-black font-medium">Home</a>
                </li>
                <li
                    class="flex justify-center items-center py-1 px-2 w-[90px] rounded-[0.5rem]"
                >
                    <a href="" class="p-0 m-0 text-white font-medium"
                        >Services</a
                    >
                </li>
                <li
                    class="flex justify-center items-center py-1 px-2 w-[90px] rounded-[0.5rem]"
                >
                    <a href="" class="p-0 m-0 text-white font-medium">Sandbox</a
                    >
                </li>
                <li
                    class="flex justify-center items-center py-1 px-2 w-[90px] rounded-[0.5rem]"
                >
                    <a href="" class="p-0 m-0 text-white font-medium"
                        >Writings</a
                    >
                </li>

                <li
                    class="flex justify-center items-center py-1 px-2 w-[90px] rounded-[0.5rem]"
                >
                    <a href="" class="p-0 m-0 text-white font-medium">Stack</a>
                </li>
            </div>
        </ul>
    </nav>

    <slot class="max-w-[500px]"></slot>
</main>
