<script setup>
const router = useRouter();
const client = useSupabaseAuthClient();
const user = useSupabaseUser();

const credentials = reactive({
    email: "",
    password: ""
});

// Log into account
async function login() {
    const {email, password} = credentials;
    const {error} = await client.auth.signInWithPassword({email, password});
    if(!error) return router.push("/");
    console.log(error)
}

// Watch if the user object is not null
watchEffect(async () => {
    if(user.value){
        await router.push("/");
    }
})
</script>

<template>
    <h1>Log in to your account!</h1>
    <form @submit.prevent="login()">
        <div>
            <label for="email">Email</label>
            <input type="email" id="email" v-model="credentials.email" />
        </div>
        <div>
            <label for="password">Password</label>
            <input type="password" id="password" v-model="credentials.password" />
        </div>
        <div>
            <button type="submit" >Submit</button>
        </div>
    </form>
</template>

<style scoped>
form{
    display: flex;
    flex-direction: column;
    padding: 4px;
}
</style>