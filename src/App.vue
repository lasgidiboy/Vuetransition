<template>
  <div class="container">
    <div class="row">
      <div class="col-md-4 offset-md-4 text-center">
        <h1>Super Quiz</h1>
      </div>
    </div>
    <div class="row">
      <div class="col-md-4 offset-md-4">
        <transition name="flip" mode="out-in">
          <component
            :is="mode"
            @answered="answered($event)"
            @confirmed="mode = 'app-question'"
          ></component>
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
import Answer from "./components/Answer.vue";
import Question from "./components/Question.vue";
export default {
  data() {
    return {
      mode: "app-question"
    };
  },
  methods: {
    answered(isCorrect) {
      if (isCorrect) {
        this.mode = "app-answer";
      } else {
        this.mode = "app-question";
        alert("wrong, try again");
      }
    }
  },
  components: {
    appQuestion: Question,
    appAnswer: Answer
  }
};
</script>

<style>
.flip-enter {
  /* transform: rotateY(0deg); */
}
.flip-enter-active {
  animation: flip-in 0.5s ease-out forwards;
}
.flip-leave {
  /* transform: rotateY(0deg); */
}
.flip-leave-active {
  animation: flip-out 0.5s ease-out forwards;

}
@keyframes flip-out {
  from {
    transform: rotateY(0deg);
  }
  to {
    transform: rotateY(90deg);
  }
}
@keyframes flip-in {
  from {
    transform: rotateY(90deg);
  }
  to {
    transform: rotateY(0deg);
  }
}
</style>
