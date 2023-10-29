<template>
    <transition name="modal">
        <div class="modal" @click="$emit('closeModal')">
            <div class="modal-content" @click.stop>
                <h2>Отправить картинку</h2>
                <form @submit.prevent="send">
                    <input type="text" placeholder="URL" required v-model="imgData.url">
                    <textarea placeholder="Комментарий"  v-model="imgData.comm" rows="2"></textarea>
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
                imgData: {
                    url: '',
                    comm: ''                  
                },
            }
        },
        methods: {
            send(){
                this.$emit('addImg', {...this.imgData})
                this.$emit('closeModal')
                for (const key in this.imgData) this.imgData[key] = ''
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