<script>
import { Otzartabs } from './entry';
import {default as tabitem} from './lib-components/tab_btn.vue'
export default {
    name:  'Otzar_tabsLibDev', // vue library dev component
    components: {
        Otzartabs,
        tabitem
    },
}

</script>

<template>
    
        <otzartabs  ref="tabs">
            <tabitem>Demo 1</tabitem>
            <tabitem is_active=1>Demo 2</tabitem>
            <tabitem>Demo 3</tabitem>
        </otzartabs>
    
</template>

<style scoped>

</style>
