<template>
    <div class="ueditor">
        <div id="container" :name="name">12</div>
    </div>
</template>
<script>
    function scripts(url) {
        let script = document.createElement("script");
        script.type = "text/javascript";
        script.src = url;
        document.body.appendChild(script);
    }
    //    import config from '../../static/ueditor/ueditor.config.js';
    //    import ueditor from '../../static/ueditor/ueditor.all.min.js';
    export default {
        name: 'ueditor',
        created() {
            scripts('static/ueditor/ueditor.config.js');
            scripts('static/ueditor/ueditor.all.min.js');
            setTimeout(() => {
                let ue = UE.getEditor('container', this.ueOption);
                ue.addListener('ready', (editor) => {
                    ue.setContent(this.$slots.default[0].text);
                });
            }, 200)
        },
        props: {
            name: String,
            option: {
                type: Object,
                required: false,
                default() {
                    return {}
                }
            }
        },
        data() {
            return {
                ueOption: this.option
            }
        },
        methods: {
            options() {
                this.ueOption = Object.assign({
                    UEDITOR_HOME_URL: 'static/ueditor/',
                    serverUrl: 'aa.php',
                    'elementPathEnabled': false,
                    'initialFrameHeight': 200,
                    'focus': false,
                    'maximumWords': 9999999999999,
                    'autoClearinitialContent': false,
                    'toolbars': [['fullscreen', 'source', 'preview', '|', 'bold', 'italic', 'underline', 'strikethrough', 'forecolor', 'backcolor', '|',
                        'justifyleft', 'justifycenter', 'justifyright', '|', 'insertorderedlist', 'insertunorderedlist', 'blockquote', 'emotion',
                        'link', 'removeformat', '|', 'rowspacingtop', 'rowspacingbottom', 'lineheight', 'indent', 'paragraph', 'fontsize', '|',
                        'inserttable', 'deletetable', 'insertparagraphbeforetable', 'insertrow', 'deleterow', 'insertcol', 'deletecol',
                        'mergecells', 'mergeright', 'mergedown', 'splittocells', 'splittorows', 'splittocols', '|', 'map', 'print', 'drafts']],
                    autoHeightEnabled: false,//自动增高
                    autoFloatEnabled: false,
                }, this.ueOption);
            }
        }
    }
</script>