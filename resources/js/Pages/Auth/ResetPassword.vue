<script setup>
import Container from '../../Components/Container.vue';
import Title from '../../Components/title.vue';
import inputField from '../../Components/inputField.vue';
import PrimaryBtn from '../../Components/PrimaryBtn.vue';
import ErrorMessages from '../../Components/ErrorMessages.vue';
import { Head, useForm } from '@inertiajs/vue3';

const props = defineProps({
    token: String,
    email: String,
})

const form = useForm({
    token: props.token,
    email: props.email,
    password: '',
    password_confirmation: '',
});

const submit = () => {
    form.post(route('password.update'), {
        onFinish: () => form.reset('password', 'password_confirmation'),
    })
}

</script>

<template>
    <Head title="— Redefinir Senha"/>
    <Container class="w-1/2">
        <div class="mb-8 text-center">
            <Title>Entre com sua nova senha</Title>
        </div>

        <!-- Error Messages -->
         <ErrorMessages :errors="form.errors"/>

        <form @submit.prevent="submit" class="space-y-6">

            <inputField label="E-Mail" type="email" icon="at" v-model="form.email"/>
            <inputField label="Password" type="password" icon="key" v-model="form.password"/>
            <inputField label="Confirm Password" type="password" icon="key" v-model="form.password_confirmation"/>

            <PrimaryBtn :disabled="form.processing">Redefinir Senha</PrimaryBtn>

        </form>
    </Container>
</template>