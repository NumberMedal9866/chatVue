<template>
    <transition name="modal">
        <div class="modal" @click="$emit('closeModal')">
            <div class="modal-content" @click.stop>
                <h2>Отправить картинку</h2>
                <form @submit.prevent="send">
                    <input type="text" placeholder="URL" required v-model="imgData2.url2">
                    <textarea placeholder="Комментарий"  v-model="imgData2.comm2" rows="2"></textarea>
                    <div class="modal-btns">
                        <a href="#" @click.prevent="$emit('closeModal')">ОТМЕНА</a>
                        <button href="#">ОТПРАВИТЬ</button>
                    </div>
                </form>
            </div>
        </div>
    </transition>
</template>

<script>
    export default {
        // props: ['showModal'],
        data() {
            return {
                imgData2: {
                    url2: '',
                    comm2: ''                  
                },
            }
        },
        methods: {
            send(){
                this.$emit('addImg2', {...this.imgData2})
                this.$emit('closeModal')
                for (const key in this.imgData2) this.imgData2[key] = ''
            },
            // pushImg(){
            //     this.imgData.push({
            //         url: this.url, comm: this.comm
            //     })
            // },
            // getImg(){
            // let localUrl = localStorage.getItem('links')
            //     if (localUrl){
            //         this.imgData = JSON.parse(localUrl)
            //     }
            // }
        },
        // created() {
        //     this.getImg()
        // },
        // watch: {
        //     imgLink:{
        //         handler(ygiuyg){
        //             localStorage.setItem('links', JSON.stringify(this.imgData))
        //         },
        //         deep: true
        //     }
        // }
    }
</script>

<style lang="scss" scoped>

</style>