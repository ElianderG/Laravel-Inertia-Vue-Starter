<script setup>
import Container from '../../Components/Container.vue';
import Title from '../../Components/title.vue';
import TextLink from '../../Components/TextLink.vue';
import inputField from '../../Components/inputField.vue';
import PrimaryBtn from '../../Components/PrimaryBtn.vue';
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

        <form class="space-y-6">

            <inputField label="Nome" icon="id-badge"/>
            <inputField label="E-Mail" type="email" icon="at"/>
            <inputField label="Password" type="password" icon="key"/>
            <inputField label="Confirm Password" type="password" icon="key"/>

            <p class="text-slate-500 text-sm dark:text-slate-400">
                Ao clicar em registrar, concorda com os <TextLink routeName="home" label="Termos de Serviço"/>
            </p>

            <PrimaryBtn>Registrar</PrimaryBtn>

        </form>
    </Container>
</template>