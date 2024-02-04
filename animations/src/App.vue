<template>
  <button type="button" @click="flag = !flag">Toggle</button>
  
  <Transition name="fade" mode="out-in" appear>
    <!-- <h2 v-show="flag">Hello World!</h2> -->
  
    <h2 v-if="flag" key="main">Hello World!</h2>
    <h2 v-else="flag" key="secondary">Another hello!</h2>

    <!-- The key attribute is particularly important when using the v-if or v-for 
      directives with dynamic arrays or objects, as it helps Vue determine which 
      elements have changed and which ones have stayed the same. 
      In this case, the key attribute is set to either "main" or "secondary" 
      depending on whether the flag variable is true or false, respectively. 
      This allows Vue to efficiently update only the elements that have actually changed. -->

  </Transition>


  <Transition name="zoom" appear>
    <h2 v-if="flag">Hello!</h2>
  </Transition>

  
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
    <h2 v-if="flag">Hey</h2>
  </transition>


  <button @click="addItem">Add</button>
  
  <ul>
    <TransitionGroup name="fade">

      <li v-for="(number,index) in numbers" :key="number"
      @click="removeItem(index)">
      {{ number }}
    </li>
  </TransitionGroup>
  </ul>
</template>

<script >
 export default {
 name: 'App',
 data() {
  return {
    flag:false,
    numbers: [1,2,3,4,5],
  }
 },
 methods: {
  addItem() {
    const num = Math.floor(Math.random() * 100+1);
    const index = Math.floor(Math.random() * this.numbers.length);
    this.numbers.splice(index, 0, num);
  },
  removeItem(index) {
    this.numbers.splice(index, 1);
  },
  beforeEnter(el){
    console.log('before enter',el)
  },
  enter(el){
    console.log('enter',el)
    // const animation = el.animate([{transform:"scale3d(0,0,0)"},{}],{
    //   duration:1000,
    // });
    // animation.onfinish = () => {
    //   done();
    // };
  },
  afterEnter(el){
    console.log('after enter',el)
  },
  beforeLeave(el){
    console.log('before leave',el)
  },
  leave(el){
    console.log('leave',el)
    // const animation = el.animate([{},{transform:"scale3d(0,0,0)"}],{
    //   duration:1000,
    // });
    // animation.onfinish = () => {
    //   done();
    // };
  },
  afterLeave(el){
    console.log('after leave',el)
  },
 }
};  
</script>

<style>
li{
  font-size: 22px;
  cursor: pointer;
}
  h2 {
    width: 400px;
    padding: 20px;
    margin: 20px;
  }

.fade-enter-from {
  opacity: 0;
}

.fade-enter-active {
  transition: all 0.5s linear;
}

.fade-leave-to {
  transition: all 0.5s linear;
  opacity: 0;
}

.fade-move{
  transition: all 1s linear;
}

.fade-leave-active {
  position: absolute;
}
/*
 is a CSS rule that specifies the position of an element when it is being removed
 using the v-transition directive. In this case, the element will be positioned absolutely, 
 which means it will be removed from the DOM and leave a blank space where it was located. 
 This is useful for animations that need to occur when an element is removed from the DOM, 
 such as fade transitions.

 In general, positioning an element absolutely is a good way to ensure that it is removed 
 from the DOM and does not leave any visual artifacts.
*/


.zoom-enter-active {
  animation: zoom-in 1s linear forwards;
  transition: all 1s linear;
}

.zoom-leave-active {
  animation: zoom-out 1s linear forwards;
  transition: all 1s linear;
}

.zoom-enter-from {
  opacity: 0;
}


.zoom-leave-to {
  opacity: 0;
}

@keyframes zoom-in {
  from {
    transform: scale(0,0);
  }
  to {
    transform: scale(1,1);
  }
}

@keyframes zoom-out {
  from {
    transform: scale(1,1);
  }
  to {
    transform: scale(0,0);
  }
}


</style>

