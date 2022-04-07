<template>
    <v-text-field
        class="expanding-search mt-1 closed"
        placeholder="Search"
        prepend-inner-icon="mdi-magnify"
        filled
        dense
        clearable
    />
</template>

<script>
export default {

}
</script>

<style lang="sass">
    .expanding-search
        .v-input__slot
            &:before, &:after
                border-color: transparent !important
        &.closed
            max-width: 45px
</style>