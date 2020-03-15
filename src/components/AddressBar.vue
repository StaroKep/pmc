<template>
    <div class="root">
        <label class="label">
            <span class="caption">Address</span>
            <input v-model="inputValue" class="input" type="text" placeholder="https://example.com" />
        </label>
        <button class="submit" v-on:click="submitButtonOnClickHandler">Submit</button>
    </div>
</template>

<script>
    function submitButtonOnClickHandler() {
        this.onSetIframeSrc(this.inputValue);
    }

    export default {
        props: ['onSetIframeSrc'],
        name: 'AddressBar',
        methods: {
            submitButtonOnClickHandler,
        },
        data: () => ({
            inputValue: '',
        })
    };
</script>

<style scoped>
    .root {
        display: flex;
        align-items: center;
        justify-content: flex-start;
        height: 80px;
        box-shadow: 0 1px 5px var(--shadow-color);
        padding: 0 10px 0 20px;
        box-sizing: border-box;
    }

    .label {
        flex: 1 1 100%;
        display: flex;
        align-items: center;
        justify-content: flex-start;
        font-family: 'Consolas', sans-serif;
        font-size: 19px;
    }
    
    .caption {
        flex: 0 0;
        white-space: nowrap;
    }

    .input {
        height: 40px;
        outline: none;
        background-color: transparent;
        border: none;
        font-family: 'Consolas', sans-serif;
        font-size: 19px;
        width: 100%;
        margin-left: 10px;
        border-left: 1px solid var(--border-color);
        padding-left: 10px;
    }

    .submit {
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

    .submit:active {
        background-color: var(--active-color);
    }
</style>