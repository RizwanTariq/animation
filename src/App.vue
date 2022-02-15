<template>
  <!-- <button type="button" @click="flag = !flag">click</button> -->
  <!-- <transition name="fade" mode="out-in">
    <h1 v-if="flag" key="primary">Hello One!</h1>
    <h1 v-else key="secondary">Hello Two!</h1>
  </transition> -->
  <!-- <transition name="zoom" appear>
    <h1 v-if="flag">Hello!</h1>
  </transition> -->

  <!-- <transition
    @before-enter="beforeEnter"
    @enter="enter"
    @after-enter="afterEnter"
    @before-leave="beforeLeave"
    @leave="leave"
    @after-leave="afterLeave"
    :css="true"
    name="fade"
  >
    <h1 v-if="flag">Hook</h1>
  </transition> -->
  <button type="button" @click="addNumber">AddNumber</button>
  <ul>
    <transition-group name="fade">
      <li
        v-for="(number, index) in numbers"
        :key="number"
        @click="removeNumber(index)"
      >
        {{ number }}
      </li>
    </transition-group>
  </ul>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      flag: true,
      numbers: [1, 2, 3, 4, 5],
    };
  },
  methods: {
    addNumber() {
      this.numbers = [
        ...this.numbers,
        this.numbers[this.numbers.length - 1] + 1,
      ];
    },
    removeNumber(index) {
      this.numbers.splice(index, 1);
    },
    beforeEnter(el) {
      console.log("beforeEnter", el);
    },
    enter(el) {
      console.log("Enter", el);

      // const animate = el.animate([{ transform: "scale3d(0,0,0)" }, {}], {
      //   duration: 1000,
      // });

      // animate.onfinish = () => {
      //   done();
      // };
    },
    afterEnter(el) {
      console.log("afterEnter", el);
    },
    beforeLeave(el) {
      console.log("beforeLeave", el);
    },
    leave(el) {
      console.log("Leave", el);

      // const animate = el.animate([{}, { transform: "scale3d(0,0,0)" }], {
      //   duration: 1000,
      // });

      // animate.onfinish = () => {
      //   done();
      // };
    },
    afterLeave(el) {
      console.log("afterLeave", el);
    },
  },
};
</script>

<style>
li {
  font-size: 20px;
  cursor: pointer;
}
.fade-move {
  transition: all 1s linear;
}
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s linear;
}
.fade-leave-active {
  transition: all 1s linear;
  opacity: 0;
  position: absolute;
}
.zoom-enter-active {
  animation: zoom-in 1s linear forwards;
}
.zoom-leave-active {
  animation: zoom-out 1s linear;
}

@keyframes zoom-in {
  from {
    transform: scale(0, 0);
  }
  to {
    transform: scale(1, 1);
  }
}
@keyframes zoom-out {
  from {
    transform: scale(1, 1);
  }
  to {
    transform: scale(0, 0);
  }
}
</style>
