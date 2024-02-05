<template>
     <h1>Home Page</h1>
</template>

<script >
export default {
    name: 'Home',
    unmounted() {
        console.log('Home page unmounted');
    },
    activated() {
        console.log('Home page activated');
    },
    deactivated() {
        console.log('Home page deactivated');
    },
    
}

</script>

