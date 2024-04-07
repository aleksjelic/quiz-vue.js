<script setup>
    import Question from '../components/Question.vue'
    import QuizHeader from '@/components/QuizHeader.vue'
    import {useRoute} from 'vue-router'
    import { computed, ref } from 'vue'
    import quizes from "@/data/quizes.json"
    import { watch } from 'vue'
    import Result from '@/components/Result.vue'
    const route=useRoute()
    const quizId=parseInt(route.params.id)
    const currentQuestionIndex=ref(0)
    const quiz=quizes.find(q => q.id===quizId)
    const brojTacnihOdgovora=ref(0);
    const prikaziRezultat=ref(false);

    // const questionStatus=ref(`${currentQuestionIndex.value}/${quiz.questions.length}`)
    // watch(()=>currentQuestionIndex.value,()=>{
    //     questionStatus.value=`${currentQuestionIndex.value}/${quiz.questions.length}`
        

    // })
    const questionStatus=computed(()=>`${currentQuestionIndex.value}/${quiz.questions.length}`)
    const procenat=computed(()=> `${currentQuestionIndex.value/quiz.questions.length*100}%`)
    const onOptionSelected=(isCorrect) => {
        if(isCorrect){
            brojTacnihOdgovora.value++;
        }
        if(quiz.questions.length-1 ===currentQuestionIndex.value){
            prikaziRezultat.value=true
        }
        currentQuestionIndex.value++;
    }
</script>

<template>  
    <div>
        {{ questionStatus }}
        {{ procenat }}
        {{ brojTacnihOdgovora }}
        
        <div>
            
            <QuizHeader :questionStatus="questionStatus" :procenat="procenat"
                        
            />
        </div>
        
        <div>
            <Question v-if="!prikaziRezultat" :question="quiz.questions[currentQuestionIndex]" @selectOption="onOptionSelected" />
            <Result v-else :ukupanBrojPitanja="quiz.questions.length" :brojTacnihOdgovora="brojTacnihOdgovora"/>
        </div>
            

    </div>
</template>
<style scoped>
    
</style>