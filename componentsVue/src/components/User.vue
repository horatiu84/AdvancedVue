<template>
    <button type="button" @click="onClickAge">Update age</button>
    <button type="button" @click="ageChangeFN(3)">Update age CB</button>
    <p>The user is {{ age }} years old</p>
    <p>{{ ageDoubled }}</p>
</template>

<script>
    export default {
        name: 'User',
        props: {
            age: {
                type: Number,
                required:true,
                default:20,
                validator(value) {
                    return value < 130;
                }
            },
            ageChangeFN: Function
        },
        /*

        The props option in the component definition is used to define the properties that the component accepts.
        In this case, the "User" component accepts a prop called "age", which has a type of Number, is required, 
        has a default value of 20, and a validator function that ensures the value is less than 130.

        The type option is used to specify the type of data that the prop accepts. 
        In this case, the prop accepts only numbers.

        The required option is used to specify whether the prop is required or not. 
        In this case, the prop is required, which means that the parent component must provide a value for the prop.

        The default option is used to specify a default value for the prop if no value is provided by the parent component. 
        In this case, the default value is 20. (optional here since is required)

        The validator option is used to specify a custom validator function for the prop. 
        In this case, the validator function is a custom function that ensures the value of the prop is less than 130. 
        If the value is greater than or equal to 130, the validator function will return false, 
        which will cause the component to throw an error.

        */
        emits:['age-change'],
        /*
        The emits option in the component definition tells Vue that the component emits an event called "age-change".
        This is used to communicate between the parent component and the child component. 
        In this case, the parent component can listen for the "age-change" event and react accordingly.

        In this example, the "User" component emits an "age-change" event whenever the "onClickAge" method is called. 
        This allows the parent component to listen for the "age-change" event and update its own state accordingly.
        */
        computed: {
            ageDoubled() {
                return this.age * 2;
            }
        },
        methods: {
            onClickAge() {
                /*
                The $emit method is a built-in method in Vue.js that is used to emit an event from a component. 
                In this case, the "age-change" event is being emitted with a value of 3, which can be listened 
                for by the parent component and reacted to accordingly.
                */
                this.$emit('age-change',3);
            }
        }

    }
</script>
