<script setup>
import { Head, Link, useForm } from "@inertiajs/inertia-vue3";
import JetAuthenticationCard from "@/Jetstream/AuthenticationCard.vue";
import JetAuthenticationCardLogo from "@/Jetstream/AuthenticationCardLogo.vue";
import JetButton from "@/Jetstream/Button.vue";
import JetInput from "@/Jetstream/Input.vue";
import JetCheckbox from "@/Jetstream/Checkbox.vue";
import JetLabel from "@/Jetstream/Label.vue";
import JetValidationErrors from "@/Jetstream/ValidationErrors.vue";
import { ref } from "vue";

const form = useForm({
    name: "",
    email: "",
    password: "",
    password_confirmation: "",
    terms: false,
});

const inappropriateName = ref(false);

const submit = () => {
    // check if bad words are in the name
    if (swearFilter.isProfane(form.name)) {
        inappropriateName.value = true;
        return;
    }

    form.post(route("register"), {
        onFinish: () => form.reset("password", "password_confirmation"),
    });
};
</script>

<template>
    <Head title="Register" />
    <div
        class="items-top justify-center min-h-screen bg-gray-100 dark:bg-gray-900 sm:items-center sm:pt-0"
        style="padding-bottom: 25px"
    >
        <Container>
            <JetAuthenticationCard>
                <div class="text-center">
                    <h1 class="leading-none text-2xl text-grey-darkest mb-3">
                        <p
                            class="no-underline text-grey-darkest hover:text-black dark:text-white"
                        >
                            <span class="dark:text-white">Rota App</span>
                        </p>
                    </h1>

                    <p>Register blurb</p>
                </div>

                <Alert
                    v-if="inappropriateName"
                    variant="warning"
                    class="my-4"
                    :message="t('register.badLanguage')"
                />

                <form @submit.prevent="submit">
                    <div>
                        <JetLabel for="name" value="Name" />
                        <JetInput
                            id="name"
                            v-model="form.name"
                            type="text"
                            class="mt-1 block w-full"
                            required
                            autofocus
                            autocomplete="name"
                        />
                    </div>

                    <div class="mt-4">
                        <JetLabel for="email" value="Email" />
                        <JetInput
                            id="email"
                            v-model="form.email"
                            type="email"
                            class="mt-1 block w-full"
                            required
                        />
                    </div>

                    <div class="mt-4">
                        <JetLabel for="password" value="Password" />
                        <JetInput
                            id="password"
                            v-model="form.password"
                            type="password"
                            class="mt-1 block w-full"
                            required
                            autocomplete="new-password"
                        />
                    </div>

                    <div class="mt-4">
                        <JetLabel
                            for="password_confirmation"
                            value="Confirm Password"
                        />
                        <JetInput
                            id="password_confirmation"
                            v-model="form.password_confirmation"
                            type="password"
                            class="mt-1 block w-full"
                            required
                            autocomplete="new-password"
                        />
                    </div>

                    <div class="flex items-center justify-end mt-4">
                        <Link
                            :href="route('login')"
                            class="underline text-sm text-gray-600 hover:text-gray-900"
                        >
                            Already registered?
                        </Link>

                        <JetButton
                            class="ml-4"
                            :class="{ 'opacity-25': form.processing }"
                            :disabled="form.processing"
                        >
                            Register
                        </JetButton>
                    </div>
                </form>
            </JetAuthenticationCard>
        </Container>
    </div>
</template>
