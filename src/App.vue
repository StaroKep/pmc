<template>
    <div id="app">
        <AddressBar :onSetIframeSrc="setIframeSrc" />
        <iFrame v-bind:iframeSrc="iframeSrc" />
        <Console />
    </div>
</template>

<script>
import AddressBar from './components/AddressBar.vue';
import iFrame from './components/iFrame.vue';
import Console from './components/Console.vue';

function setIframeSrc(url) {
    this.iframeSrc = url;
}

export default {
    name: 'App',
    components: {
        AddressBar,
        iFrame,
        Console,
    },
    data: () => ({
        iframeSrc: '',
    }),
    methods: {
        setIframeSrc,
    }
};
</script>

<style>
    * {
        font-size: 17px;
        font-family: 'Arial', sans-serif;
    }

    body {
        margin: 0;
        background-color: var(--page-background-color);
        padding-bottom: var(--console-height);
    }
</style>