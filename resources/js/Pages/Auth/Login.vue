<script setup>
import Container from '../../Components/Container.vue';
import Title from '../../Components/title.vue';
import TextLink from '../../Components/TextLink.vue';
import inputField from '../../Components/inputField.vue';
import PrimaryBtn from '../../Components/PrimaryBtn.vue';
import ErrorMessages from '../../Components/ErrorMessages.vue';
import CheckBox from '../../Components/CheckBox.vue';
import { Head, useForm } from '@inertiajs/vue3';


const form = useForm({
    email: '',
    password: '',
    remember: null,
});

const submit = () => {
    form.post(route('login'), {
        onFinish: () => form.reset('password'),
    })
}

</script>

<template>
    <Head title="— Login"/>
    <Container class="w-1/2">
        <div class="mb-8 text-center">
            <Title> Logue em sua conta </Title>
            <p>
                Precisa de uma conta? 
                <TextLink routeName="register" label="Registre-se"/>
            </p>
        </div>

        <!-- Error Messages -->
         <ErrorMessages :errors="form.errors"/>

        <form @submit.prevent="submit" class="space-y-6">

            <inputField label="E-Mail" type="email" icon="at" v-model="form.email"/>
            <inputField label="Password" type="password" icon="key" v-model="form.password"/>

            <div class="flex items-center justify-between">
                <CheckBox name="remember" v-model="form.remember">Lembrar de mim</CheckBox>
                <TextLink routeName="home" label="Esqueceu sua senha?"/>
            </div>

            <PrimaryBtn :disabled="form.processing">Login</PrimaryBtn>

        </form>
    </Container>
</template>