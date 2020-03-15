<template>
    <div class="root">
        <iframe class="iframe" :src="iframeSrc || defaultIframeSrc"/>
    </div>
</template>

<script>
    const defaultIframeSrc = 'https://starokep.github.io/pmc/dist/example.html';

    export default {
        props: ['iframeSrc'],
        name: 'iFrame',
        data: () => ({
            defaultIframeSrc,
        })
    };
</script>

<style scoped>
    .root {
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .iframe {
        width: 1024px;
        height: 768px;
        margin: 25px;
        border: none;
        border-radius: 5px;
        background: linear-gradient(-45deg, rgba(220,220,220,1) 0%, rgba(240,240,240,1) 100%);
        box-shadow: 1px 1px 5px var(--shadow-color);
    }
</style>