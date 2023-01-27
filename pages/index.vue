<script setup>
const user = useSupabaseUser();
const router = useRouter();
definePageMeta({
    middleware: 'auth'
})
watchEffect(async () => {
    if(!user.value){
        await router.push("/login");
    }
})
</script>

<template>
    <h1>Welcome to the dashboard!</h1>
</template>