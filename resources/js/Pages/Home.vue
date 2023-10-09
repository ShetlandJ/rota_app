<template>
    <div
        class="items-top justify-center min-h-screen bg-gray-100 dark:bg-gray-900 sm:items-center sm:pt-0"
        style="padding-bottom: 25px"
    >
        <NavBar />

        <Container>
            <h4
                class="text-center text-2xl font-bold text-gray-700 dark:text-white mb-4"
            >
                Login to your account
            </h4>

            <Login class="mb-2" />
        </Container>
    </div>
</template>

<script>
import { Head } from "@inertiajs/inertia-vue3";
import Container from "../components/Container.vue";
import NavBar from "../components/NavBar.vue";
import Login from "../Pages/Auth/Login.vue";

export default {
    components: {
        Head,
        Container,
        NavBar,
        Login,
    },
    data() {
        return {};
    },
    methods: {},
    computed: {},
    created() {},
};
</script>

<style scoped>
progress::-webkit-progress-bar {
    background-color: white;
}

progress::-webkit-progress-value {
    transition: width 0.1s;
}
</style>
