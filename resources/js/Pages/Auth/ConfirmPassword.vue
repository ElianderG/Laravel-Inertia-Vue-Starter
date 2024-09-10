<script setup>
import Container from '../../Components/Container.vue';
import inputField from '../../Components/inputField.vue';
import PrimaryBtn from '../../Components/PrimaryBtn.vue';
import ErrorMessages from '../../Components/ErrorMessages.vue';
import { Head, useForm } from '@inertiajs/vue3';


const form = useForm({
    password: '',

});

const submit = () => {
    form.post(route('password.confirm'), {
        onFinish: () => form.reset(),
    });
};

</script>

<template>
    <Head title="— Confirmar Senha"/>
    <Container class="w-1/2">
        <div class="mb-8 text-center">
            <p>
                Por favor, confirme sua senha antes de continuar.
            </p>
        </div>

        <!-- Error Messages -->
         <ErrorMessages :errors="form.errors"/>

        <form @submit.prevent="submit" class="space-y-6">
            <inputField label="Password" type="password" icon="key" v-model="form.password"/>

            <PrimaryBtn :disabled="form.processing">Confirmar</PrimaryBtn>

        </form>
    </Container>
</template>