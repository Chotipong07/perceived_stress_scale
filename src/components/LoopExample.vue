<template>
      <div class="mx-auto max-w-2xl my-6 p-4 sm:px-6 lg:px-8 bg-white rounded-lg shadow ">
        <div v-for="(question, index) in questions" :key="index" class="mx-3 pt-4 pb-3 border-b-2 border-gray-300">
        <span class="font-bold mr-2">ข้อที่ {{ index + 1 }} </span><span class="font-medium">{{ question.question }}</span>
        <div class="py-3">
            <div class="flex flex-col md:flex-row py-2 px-2 sm:w-full lg:w-auto">
              <label class='radio-container'>
                <input class="animations_input" type='radio' :name="'choice_' + [index + 1]" @change="calculateScore($event, index, 1)" v-model="question.selectedAnswer"  :value="question.never">
                <span class='pl-2 pr-6'>ไม่เลย</span>          
              </label>
              <label class='radio-container'>
                <input class='animations_input' type='radio' :name="'choice_' + [index + 1]" @change="calculateScore($event, index, 2)" v-model="question.selectedAnswer"  :value="question.middle">
                <span class='pl-2 pr-6'>เล็กน้อย</span>          
              </label>
              <label class='radio-container'>
                <input class='animations_input' type='radio' :name="'choice_' + [index + 1]" @change="calculateScore($event, index, 3)" v-model="question.selectedAnswer"  :value="question.big">
                <span class='pl-2 pr-6'>มาก</span>          
              </label>
              <label class='radio-container'>
                <input class='animations_input' type='radio' :name="'choice_' + [index + 1]" @change="calculateScore($event, index, 4)" v-model="question.selectedAnswer"  :value="question.biggest">
                <span class='pl-2 pr-6'>มากที่สุด</span>          
              </label>
            </div>
        </div>
      </div>
      <div class="text-center my-5 ">
      <button class="px-4 py-2 bg-indigo-500 text-white rounded"  v-on:click="doSomething">ส่งแบบสอบถาม</button>
    </div>
    </div>

    
</template>
  
<script>
import axios from 'axios';
import Swal from 'sweetalert2'
export default {
  data() {
    return {
      totalScore: 0,
      user:{
        user_info:{
          user_first_name:'อลิซ',
          user_last_name:'แซมเบอร์ก',
          user_id_card:406,
          user_total:null,
          user_data:'2023-07-22 11:10:00',
        }
      },
      answered: {
          question1: {
            answer_timestamp: '2023-07-22 11:10:00',
            answer_choice: 1,
            answer_score: 3
        },
        question2: {
            answer_timestamp: '2023-07-22 11:10:00',
            answer_choice: 1,
            answer_score: 3
        },
        question3: {
            answer_timestamp: '2023-07-22 11:10:00',
            answer_choice: 1,
            answer_score: 3
        },
        question4: {
            answer_timestamp: '2023-07-22 11:10:00',
            answer_choice: 1,
            answer_score: 3
        },
        question5: {
            answer_timestamp: '2023-07-22 11:10:00',
            answer_choice: 1,
            answer_score: 3
        },
        question6: {
            answer_timestamp: '2023-07-22 11:10:00',
            answer_choice: 1,
            answer_score: 3
        },
        question7: {
            answer_timestamp: '2023-07-22 11:10:00',
            answer_choice: 1,
            answer_score: 3
        },
        question8: {
            answer_timestamp: '2023-07-22 11:10:00',
            answer_choice: 1,
            answer_score: 3
        },
        question9: {
            answer_timestamp: '2023-07-22 11:10:00',
            answer_choice: 1,
            answer_score: 3
        },
        question10: {
            answer_timestamp: '2023-07-22 11:10:00',
            answer_choice: 1,
            answer_score: 3
        },
        question11: {
            answer_timestamp: '2023-07-22 11:10:00',
            answer_choice: 1,
            answer_score: 3
        },
        question12: {
            answer_timestamp: '2023-07-22 11:10:00',
            answer_choice: 1,
            answer_score: 3
        },
        question13: {
            answer_timestamp: '2023-07-22 11:10:00',
            answer_choice: 1,
            answer_score: 3
        },
        question14: {
            answer_timestamp: '2023-07-22 11:10:00',
            answer_choice: 1,
            answer_score: 3
        },
        question15: {
            answer_timestamp: '2023-07-22 11:10:00',
            answer_choice: 1,
            answer_score: 3
        },
      },
      questions: [
        {questions_id:1, never:0, middle:1, big:2, biggest:3,question: "ท่านรู้สึกว่าชีวิตของท่านมีความสุข", selectedAnswer: null },
        {questions_id:2,  never:0, middle:1, big:2, biggest:3,question: "ท่านรู้สึกภูมิใจในตนเอง", selectedAnswer: null },
        {questions_id:3,  never:3, middle:2, big:1, biggest:0,question: "ท่านต้องไปรับการรักษาพยาบาลเสมอ ๆ เพื่อให้สามารถดำเนินชีวิตและทำงานได้", selectedAnswer: null },
        {questions_id:4,  never:0, middle:1, big:2, biggest:3,question: "ท่านพึงพอใจในรูปร่างหน้าตาของท่าน", selectedAnswer: null },
        {questions_id:5,  never:0, middle:1, big:2, biggest:3,question: "ท่านมีสัมพันธภาพที่ดีกับเพื่อนบ้าน", selectedAnswer: null },
        {questions_id:6,  never:0, middle:1, big:2, biggest:3,question: "ท่านรู้สึกประสบความสำเร็จและความก้าวหน้าในชีวิต", selectedAnswer: null},
        {questions_id:7,  never:3, middle:2, big:1, biggest:0,question: "ท่านมั่นใจที่จะเผชิญกับเหตุการณ์ร้ายแรงที่เกิดขึ้นในชีวิต", selectedAnswer: null },
        {questions_id:8,  never:0, middle:1, big:2, biggest:3,question: "ถ้าสิ่งต่างๆ ไม่เป็นไปตามที่คาดหวัง ท่านจะรู้สึกหงุดหงิด", selectedAnswer: null },
        {questions_id:9,  never:0, middle:1, big:2, biggest:3,question: "ท่านสามารถปฏิบัติกิจวัตรประจำวันต่าง ๆ ด้วยตัวท่านเอง", selectedAnswer: null },
        {questions_id:10,  never:0, middle:1, big:2, biggest:3,question: "ท่านรู้สึกเป็นสุขในการช่วยเหลือผู้อื่นที่มีปัญหา", selectedAnswer: null },
        {questions_id:11,  never:0, middle:1, big:2, biggest:3,question: "ท่านมีความสุขกับการริเริ่มงานใหม่ๆ และมุ่งมั่นที่จะทำให้สำเร็จ", selectedAnswer: null },
        {questions_id:12,  never:0, middle:1, big:2, biggest:3,question: "ท่านรู้สึกว่าชีวิตของท่านไร้ค่า ไม่มีประโยชน์", selectedAnswer: null },
        {questions_id:13,  never:0, middle:1, big:2, biggest:3,question: "ท่านมีเพื่อนหรือญาติพี่น้องคอยช่วยเหลือท่านในยามที่ท่านต้องการ", selectedAnswer: null },
        {questions_id:14,  never:0, middle:1, big:2, biggest:3,question: "ท่านมั่นใจว่าชุมชนที่ท่านอยู่อาศัยมีความปลอดภัยต่อท่าน", selectedAnswer: null },
        {questions_id:15,  never:0, middle:1, big:2, biggest:3,question: "ท่านมีโอกาสได้พักผ่อนคลายเครียด", selectedAnswer: null },
        // เพิ่มข้อมูลเพิ่มเติมตามต้องการ
      ],
    totalScore: null,
    assessment: null,
    };
  }, methods: {
    calculateScore(e, index, choice) {

      let date = new Date

      this.totalScore = 0

      this.answered[`question${index + 1}`] = {}

      this.answered[`question${index + 1}`].answer_timestamp = date
      this.answered[`question${index + 1}`].answer_choice = choice
      this.answered[`question${index + 1}`].answer_score = e.target.value

      this.questions.map(item => item.selectedAnswer).filter(item => item != null).forEach(item => this.totalScore += item);
      // console.log(this.totalScore);
      // console.log(this.answered);

      
      if (this.totalScore >= 0 && this.totalScore <= 20) {
        this.assessment = "มีความสุขน้อยกว่าคนทั่วไป ";
      } else if (this.totalScore >= 21 && this.totalScore <= 40) {
        this.assessment = "มีความสุขเท่ากับคนทั่วไป ";
      } else if (this.totalScore >= 44 && this.totalScore <= 60) {
        this.assessment = "มีความสุขมากกว่าคนทั่วไป ";
      } else {
        this.assessment = "สุขภาพดีมาก";
      }

    },
    calculateTotalSelectedAnswer() {
      return this.questions.reduce((total, question) => {
        if (question.selectedAnswer !== null) {
          total += parseInt(question.selectedAnswer, 10);
        }
        return total;
      }, 0);
    },

    isAllQuestionsAnswered() {
      return this.questions.every(question => question.selectedAnswer !== null);
    },

    doSomething() {
      if (this.isAllQuestionsAnswered()) {
        this.totalScore = this.calculateTotalSelectedAnswer();
        // ส่วนอื่น ๆ ของฟังก์ชัน doSomething()
        Swal.fire({
          title: 'คะแนนทั้งหมดคือ: ' + this.totalScore,
          text: 'การประเมิน: ' + this.assessment,
          icon: 'success',
        });
      } else {
        Swal.fire({
          title: 'แจ้งเตือน',
          text: 'กรุณาตอบคำถามทุกข้อก่อนแสดงคะแนน',
          icon: 'warning',
        });
      }
    },
  },
};
</script>

<style>
.animations_input[type="radio"] {
	appearance: none;
	-webkit-appearance: none;
	width: 20px;
	height: 20px;
	border: 2px solid #5c5c5c;
	border-radius: 50%;
	margin-right: 10px;
	background-color: transparent;
	position: relative;
}

.animations_input[type="radio"]:checked::before {
	content: "";
	display: block;
	width: 11px;
	height: 11px;
	background-color: #657dff;
	border-radius: 50%;
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
	animation: appear 0.8s;
}

@keyframes appear {
	0% {
		transform: translate(-50%, -50%) scale(0);
		background-color: #fff;
	}
	45% {
		transform: translate(-50%, -50%) scale(1.6);
		background-color: #64aedf;
	}
	50% {
		transform: translate(-50%, -50%) scale(1.7);
		background-color: #809fd8;
	}
	55% {
		transform: translate(-50%, -50%) scale(1.6);
	}
	100% {
		transform: translate(-50%, -50%) scale(1);
		background-color: #4596ff;
	}
}

</style>