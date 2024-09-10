<script setup>
import Container from '../../Components/Container.vue';
import inputField from '../../Components/inputField.vue';
import PrimaryBtn from '../../Components/PrimaryBtn.vue';
import ErrorMessages from '../../Components/ErrorMessages.vue';
import SessionMessages from '../../Components/SessionMessages.vue';
import { Head, useForm } from '@inertiajs/vue3';

defineProps({status: String})

const form = useForm({
    email: '',
});

const submit = () => {
    form.post(route('password.email'));
}

</script>

<template>
    <Head title="— Forgot Password"/>
    <Container class="w-1/2">
        <div class="mb-8 text-center">
            <p>
                Esqueceu sua senha? Sem problemas. Basta nos informar seu endereço de e-mail e enviaremos um link para redefinir sua senha.
            </p>
        </div>

        <!-- Error Messages -->
         <ErrorMessages :errors="form.errors"/>

        <SessionMessages :status="status"/>

        <form @submit.prevent="submit" class="space-y-6">

            <inputField label="E-Mail" type="email" icon="at" v-model="form.email"/>

            <PrimaryBtn :disabled="form.processing">Enviar Link</PrimaryBtn>

        </form>
    </Container>
</template>