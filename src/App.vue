<template>
  <button type="button" @click="flag = !flag">click</button>
  <!-- <transition name="fade" mode="out-in">
    <h1 v-if="flag" key="primary">Hello One!</h1>
    <h1 v-else key="secondary">Hello Two!</h1>
  </transition> -->
  <!-- <transition name="zoom" appear>
    <h1 v-if="flag">Hello!</h1>
  </transition> -->

  <transition
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
  </transition>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      flag: true,
    };
  },
  methods: {
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
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s linear;
}
.fade-leave-active {
  transition: all 1s linear;
  opacity: 0;
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
