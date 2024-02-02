
<template>
 <h3>Hey!</h3>

 <!-- The <greeting :age="age"></greeting> tag is an example of a component in Vue.js. 
  In this case, the component is called "Greeting" and it takes a prop called "age".
  The value of the prop "age" is passed into the component as a binding, which means 
  that the component will display the value of the prop in its template.

 In this case, the "age" prop is being passed into the component from the parent component, 
 which means that the value of the prop will be determined by the parent component. 
 In this example, the parent component is the App component, which is setting the value 
 of the "age" prop to 20.  -->
 <greeting :age="age"></greeting>


 <!--The "@age-change" attribute is an example of a listener in Vue.js, 
  which means that the component will listen for an event with the name "age-change" 
  and execute the "updateAge" method when that event is triggered. 
  In this example, the "User" component is listening for the "age-change" event from 
  the parent component, which means that the "updateAge" method will be executed whenever 
  the parent component changes the value of the "age" prop.-->
 <user :age="age"  @age-change="updateAge"  ></user>

</template>

<script >

import Greeting from './components/Greeting.vue';
import User from './components/User.vue';

export default {
  name: 'App',
  components: {
    Greeting,
    User
  },
  data() { 
    return {
      age: 20
    }
  },
  methods: {
    updateAge(num) {
      this.age += num;
    }
  },
  watch: {
    age(newAge) {
      if (newAge >125) {
        this.age = 125;
      }
    }
  }
}
</script >


