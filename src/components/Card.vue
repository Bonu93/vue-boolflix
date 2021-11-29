<template>
    <ul>
        <li>Titolo: {{ title }}</li>
        <li>Titolo originale: {{ orTitle }}</li>
        <li>Lingua: {{ language }}</li>
        <li>Voto: {{ vote }}</li>
    </ul>
</template>

<script>
export default {
    name: 'Card',
    props: {
        title: String,
        orTitle: String,
        language: String, 
        vote: Number,
    },
}
</script>

<style lang="scss" scoped>

</style>