<template>
    <div class="root" v-bind:class="{ 'root-visible': isVisibleConsole }">
        <div class="caption-area">
            <button class="post-messages-button" v-on:click="postMessagesOnClickHandler">
                {{isVisibleConsole ? 'Hide' : 'Show' }} post messages
            </button>
        </div>
        <div class="console-data">{{postMessages}}</div>
    </div>
</template>

<script>
    const state = {
        isVisibleConsole: false,
        postMessages: [],
    };

    function postMessagesOnClickHandler() {
        this.isVisibleConsole = !this.isVisibleConsole;
    }

    export default {
        name: 'Console',
        mounted() {
            window.addEventListener('message', event => {
                this.postMessages.push(event);
                console.log(this)
            })
        },
        methods: {
            postMessagesOnClickHandler,
        },
        data: () => state,
    };
</script>

<style scoped>
    .root {
        position: fixed;
        height: 35vh;
        width: 100%;
        bottom: calc(-35vh + 60px);
        z-index: 1;
        box-shadow: 0 -1px 5px var(--shadow-color);
        background-color: var(--page-background-color);
        transition-duration: .3s;
        transition-property: bottom;
    }

    .root-visible {
        bottom: 0;
    }

    .caption-area {
        width: 100%;
        height: 60px;
        display: flex;
        justify-content: flex-end;
        align-items: center;
    }

    .post-messages-button {
        background: var(--accent-color);
        color: white;
        padding: 10px 20px;
        margin: 0 10px;
        border: 1px solid var(--active-color);
        border-radius: 5px;
        outline: none;
        cursor: pointer;
        box-sizing: border-box;
    }

    .post-messages-button:active {
        background-color: var(--active-color);
    }

    .console-data {
        font-family: 'Consolas', sans-serif;
    }
</style>