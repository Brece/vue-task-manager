<template>
    <button @click="onClick()" :style="{ background: color }" class="btn">{{ text }}</button>
</template>

<script>
    export default {
        name: 'ButtonComponent',
        props: {
            text: String,
            color: String,
        },
        methods: {
            onClick() {
                // TODO: handle click event
                console.log('clicked');
            }
        }
    }
</script>
