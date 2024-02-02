<template>
    <p v-if="age > 25">{{ msg }}</p>
    <p v-else>You must be 25 years of older to see this paragraf </p>
</template>

<script>
export default {
    name: 'Greeting',
    props: ['age'],
    data() {
        return {
            msg: 'Hello'
        }
    }
}
</script>

<style scoped lang="scss">
p {
    color: #cc4444;
}
p:hover {
    color: darken(#cc4444,15%);
}

</style>