<script setup>
import Container from '../../Components/Container.vue';
import Title from '../../Components/title.vue';
import TextLink from '../../Components/TextLink.vue';
import inputField from '../../Components/inputField.vue';
import PrimaryBtn from '../../Components/PrimaryBtn.vue';
import ErrorMessages from '../../Components/ErrorMessages.vue';
import { useForm } from '@inertiajs/vue3';


const form = useForm({
    name: '',
    email: '',
    password: '',
    password_confirmation: '',
});

const submit = () => {
    form.post(route('register'), {
        onFinish: () => form.reset('password', 'password_confirmation'),
    })
}

</script>

<template>
    <Container class="w-1/2">
        <div class="mb-8 text-center">
            <Title>Registre uma nova conta</Title>
            <p>
                Já possui uma conta? 
                <TextLink routeName="home" label="login"/>
            </p>
        </div>

        <!-- Error Messages -->
         <ErrorMessages :errors="form.errors"/>

        <form @submit.prevent="submit" class="space-y-6">

            <inputField label="Nome" icon="id-badge" v-model="form.name"/>
            <inputField label="E-Mail" type="email" icon="at" v-model="form.email"/>
            <inputField label="Password" type="password" icon="key" v-model="form.password"/>
            <inputField label="Confirm Password" type="password" icon="key" v-model="form.password_confirmation"/>

            <p class="text-slate-500 text-sm dark:text-slate-400">
                Ao clicar em registrar, concorda com os <TextLink routeName="home" label="Termos de Serviço"/>
            </p>

            <PrimaryBtn :disabled="form.processing">Registrar</PrimaryBtn>

        </form>
    </Container>
</template>