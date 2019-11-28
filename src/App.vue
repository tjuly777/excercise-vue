<template>
    <div>
        <myheader></myheader>
        
        <!--v-modelディレクティブにデータ名を指定すると、値が連動 -->
        <input type="text" v-model="msg">
        
        <!--v-ifディレクティブによるif文で、タグ単位の条件分岐が可能-->
        <p v-if="msg.length > 0">{{msg}}</p>
        <p v-else>no text.</p>
        
        <button @click="clear()">Clear!</button>
        <button @click="getGeoNames()">Get GeoName!</button>
    </div>
</template>

<script>
    /* 他ファイルに分けたコンポーネントをインスタンス化 */
    import myheader from './components/myheader'
    
    /* デフォルトエクスポート */
    export default {
        /* コンポーネントを宣言し、タグ名として指定すると展開。 */
        components: {
            myheader
        },
        
        /* データバインディング */
        data() {
            return {
                msg: "It's a Sample."
            }
        },
        
        /* メソッドの宣言 */
        methods: {
            clear() {
                this.msg = ''
            },
            getGeoNames(){
                fetch('http://www.geonames.org/postalCodeLookupJSON?postalcode=10504&country=US')
                    .then( respons => {
                        return respons.json()
                    })
                    .then(json => {
                        this.msg = json.postalcodes[0].adminName1
                    })
                    .catch((err) => {
                        this.msg = err
                    })
            }
        },
        
        /* インスタンス生成直後、同期的に呼ばれる処理（ライフサイクルフックの一種） */
        created() {
            this.getGeoNames()
        }
    }
</script>
