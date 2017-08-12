<template>
    <div id="app">
        <form action="">
            <ueditor name="body">okk....</ueditor>
            <button>send</button>
        </form>
    </div>
</template>
<script>
    import ueditor from '@/components/ueditor.vue';
    export default {
        name: 'app',
        components: { ueditor},
        data(){
            return {
                cc:'33'
            }
        }
    }
</script>