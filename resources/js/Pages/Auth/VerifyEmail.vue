<script setup>
import { Head, useForm } from '@inertiajs/vue3';
import Container from '../../Components/Container.vue';
import PrimaryBtn from '../../Components/PrimaryBtn.vue';
import SessionMessages from '../../Components/SessionMessages.vue';

const form = useForm({})

defineProps({
    status: String,
})

const submit = () => {
    form.post(route('verification.send'));
}
</script>

<template>
    <Head title="— Email Verification"/>

    <Container class="w-1/2">
        <div class="mb-8">
            <p>
                Obrigado por se registrar! Antes de começar, poderia verificar
                seu email comprovando que recebeu um link de verificação? 
                Se não recebeu, enviaremos outro link de verificação.
            </p>
        </div>

        <SessionMessages :status="status"/>

        <form @submit.prevent="submit">
            <PrimaryBtn :disabled="form.processing">Reenviar verificação</PrimaryBtn>
        </form>
    </Container>    
</template>