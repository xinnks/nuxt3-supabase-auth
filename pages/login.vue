<template>
    <h1>Log in to your account!</h1>
    <form>
        <div>
            <label for="email">Email</label>
            <input type="email" id="email" />
        </div>
        <div>
            <label for="password">Password</label>
            <input type="password" id="password" />
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