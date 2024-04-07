<script setup>
import { useRouter } from 'vue-router'
const {quiz}=defineProps(['quiz'])
const router=useRouter()
const navigateToQuiz=()=>{
    router.push(`/quiz/${quiz.id}`)
}
</script>

<template>
    <div class="card" @click="navigateToQuiz">
        <img :src="quiz.img">
        <div class="card-text">
            <h2>{{quiz.name }}</h2>
            <p>{{ quiz.questions.length }} questions</p>
    
        </div>
    </div>
</template>

