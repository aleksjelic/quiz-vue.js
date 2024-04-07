<template>
    <div class="result">
        <p>Your result...</p>
        <h1>{{brojTacnihOdgovora}}/{{ukupanBrojPitanja }}</h1>
        <RouterLink to="/">Go Back</RouterLink>
    </div>
</template>
<style scoped>
.result{
    text-align: center;
    padding: 100px 0;
}
p{
    font-size: 25px;
}
h1{
    font-size: 80px;
}
</style>
<script setup>
import { defineProps } from 'vue';
const{ukupanBrojPitanja, brojTacnihOdgovora}=defineProps(["ukupanBrojPitanja","brojTacnihOdgovora"])
import {RouterLink} from "vue-router"
</script>