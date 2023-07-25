<template>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=TH+Sarabun+New&display=swap">
    <Questionnaire ></Questionnaire>
</template>

<script>
// @ is an alias to /src
import Questionnaire from '@/components/Questionnaire.vue'
import Explanation from '@/components/Explanation.vue'

export default {
  name: 'HomeView',
  components: {
    Questionnaire,
    Explanation 
  }
}


</script>
