<template>
    <v-text-field
    class="expanding-search mt-1"
        placeholder="Search"
        prepend-inner-icon="mdi-magnify"
        filled
        dense
        clearable
    ></v-text-field>
</template>

<script>
export default {

}
</script>

<style lang="sass">
    .expanding-search
        .v-input__slot
            &:before, &:after
                border-colot: transparent !important
</style>