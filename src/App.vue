<template>
    <div>
        <myheader></myheader>
        
        <!--v-modelにバインディングしたデータ名を指定すると、値が連動 -->
        <input type="text" v-model="msg">
        
        <!--v-ifによるif文で、タグ単位の条件分岐が可能-->
        <p v-if="msg.length > 0">{{msg}}</p>
        <p v-else>no text.</p>
        
        <button @click="clear()">Clear!</button>
    </div>
</template>

<script>
    import myheader from './components/myheader'
    export default {
        /*コンポーネントを宣言し、タグ名として指定すると展開。*/
        components: {
            myheader
        },
        
        /*データバインディング*/
        data() {
            return {
                msg: "It's a Sample."
            }
        },
        /*メソッドの宣言*/
        methods: {
            clear() {
                this.msg = ''
            }
        }
    }
</script>
