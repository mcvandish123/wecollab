<script setup lang="ts">
import InputError from '@/components/InputError.vue';
import TextLink from '@/components/TextLink.vue';
import { Button } from '@/components/ui/button';
import { Input } from '@/components/ui/input';
import { Label } from '@/components/ui/label';
import AuthBase from '@/layouts/AuthLayout.vue';
import { Form, Head } from '@inertiajs/vue3';
import { LoaderCircle } from 'lucide-vue-next';
</script>

<template>
    <div class="flex justify-center mb-auto border-top gap-2">
        <img src="/images/logo.png" alt="Logo" class="h-20 w-20 object-contain" />
    </div>
    <AuthBase title="Create an account" description="Sign up">
        <Head title="Register" />
        <div class="mx-auto max-w-md w-full bg-white shadow-lg p-8 rounded-2xl text-black mb-100">
            <Form
                method="post"
                :action="route('register')"
                :reset-on-success="['password', 'password_confirmation']"
                v-slot="{ errors, processing }"
                class="flex flex-col gap-6"
            >
                <div class="grid gap-6">
                    <div class="grid gap-2">
                        <Label for="name">Name</Label>
                        <Input id="name" type="text" required autofocus :tabindex="1" autocomplete="name" name="name" placeholder="Full name" class="placeholder:text-black" />
                        <InputError :message="errors.name" />
                    </div>

                    <div class="grid gap-6">
                        <Label for="email">Email address</Label>
                        <Input id="email" type="email" required :tabindex="2" autocomplete="email" name="email" placeholder="email@example.com" class="placeholder:text-black" />
                        <InputError :message="errors.email" />
                    </div>

                    <div class="grid gap-2">
                        <Label for="password">Password</Label>
                        <Input id="password" type="password" required :tabindex="3" autocomplete="new-password" name="password" placeholder="Password" class="placeholder:text-black" />
                        <InputError :message="errors.password" />
                    </div>

                    <div class="grid gap-2">
                        <Label for="password_confirmation">Confirm password</Label>
                        <Input
                            id="password_confirmation"
                            type="password"
                            required
                            :tabindex="4"
                            autocomplete="new-password"
                            name="password_confirmation"
                            placeholder="Confirm password"
                            class="placeholder:text-black"
                        />
                        <InputError :message="errors.password_confirmation" />
                    </div>

                    <div class="bg-gray-200 rounded-lg p-4 flex justify-center">
                        <Button
                            type="submit"
                            class="w-full mt-2 bg-gray-600 text-white transition-none cursor-pointer"
                            tabindex="5"
                            :disabled="processing"
                            style="background-color: #4B5563 !important; color: #fff !important;"
                        >
                            <LoaderCircle v-if="processing" class="w-4 h-4 animate-spin" />
                            Create account
                        </Button>
                    </div>
                </div>

                <div class="text-sm text-center">
                    Already have an account?
                    <TextLink :href="route('login')" class="underline underline-offset-4 text-red-600" :tabindex="6">Log in</TextLink>
                </div>
            </Form>
        </div>
    </AuthBase>
</template>

