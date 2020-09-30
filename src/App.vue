<template>
<div id="app">
  <div class="container">
    <randomcat></randomcat>
    </div>
</div>
</template>

<script>
import randomcat from './components/RandomCat.vue'
export default {
    data() {
        return {};
    },
    // computed: {},
    methods: {
        // -- Metodos
    },
    components: {
        'randomcat': randomcat,
    },

}
</script>