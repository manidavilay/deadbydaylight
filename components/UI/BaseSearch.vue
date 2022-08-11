<template>
    <section class="mx-auto mb-10 search-input">
        <slot></slot>
    </section>
</template>

<style lang="scss">
.search-input {
    width: 70%;

    @media all and (max-width: 600px) {
        width: 100%;
    }
}
</style>