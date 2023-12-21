<script setup>
import { ref } from 'vue';
import axios from 'axios';

const email = ref('');
const password = ref('');

const login = async () => {
    try {
        const res = await axios.post('http://localhost:3000/api/user/login', {
            email: email.value,
            password: password.value
        }, {
            withCredentials: true
        })
        console.log(res);
        alert('Login success')
    } catch (e) {
        alert(e.message);
    }
}
</script>

<template>
    <div>
        <form @submit.prevent="login">
            <input type="text" v-model="email">
            <input type="password" v-model="password">
            <button>Login</button>
        </form>
    </div>
</template>