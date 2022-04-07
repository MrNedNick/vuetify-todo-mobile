<template>
    <v-text-field
        @focus="searchClosed = false"
        @blur="searchClosed = true"
        class="expanding-search mt-1"
        :class="{ 'closed' : searchClosed }"
        placeholder="Search"
        prepend-inner-icon="mdi-magnify"
        filled
        dense
        clearable
    />
</template>

<script>
export default {
    data() {
        return {
            searchClosed: true
        }
    }
}
</script>

<style lang="sass">
    .expanding-search
        transition: max-width 0.3s
        .v-input__slot
            &:before, &:after
                border-color: transparent !important
        &.closed
            max-width: 45px
            .v-input__slot
                background: transparent !important
</style>