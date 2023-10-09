<script setup>
defineProps({
    narrowed: {
        type: Boolean,
        default: true,
    },
})
</script>

<template>
    <div
        class="
            bg-white
            shadow-lg
            rounded-lg
            mx-4 p-6
            md:mx-auto my-8
            dark:bg-gray-700
        "
        :class="narrowed ? 'max-w-lg md:max-w-2xl' : ''"
    >
        <slot />
    </div>
</template>