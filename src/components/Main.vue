<template>
    <div class="chat-holder">
        <div class="chat1">
            <div class="profile">
                <div class="prof-info">
                    <img src="@/assets/img/Alexander.svg" alt="">
                    <div class="prof-text">
                        <h2>Александр</h2>
                        <p>Онлайн</p>
                    </div>
                </div>
            </div>
            <div class="text-area">
                <div class="send" v-for="(message, i) in text" :key="i" :style="{order: message.id}">
                    <p>
                    {{message.text}}
                    </p>
                    <span>{{currentTime()}}</span>
                </div>
                <div class="recieve" v-for="(message2, i) in text2" :key="i" :style="{order: message2.id}">
                    <p>
                    {{message2.text2}}
                    </p>
                    <span>{{currentTime()}}</span>
                </div>
                <div class="img" v-for="(img, i) in linkImg" :key="i" :style="{order: img.id}">
                    <img :src="img.url" alt="">
                    <p v-if="img.comm.length != 0">{{img.comm}}</p>
                    <span>{{currentTime()}}</span>
                </div>
                <div class="pic" v-for="(img2, i) in linkImg2" :key="i" :style="{order: img2.id}">
                    <img :src="img2.url2" alt="">
                    <p v-if="img2.comm2.length != 0">{{img2.comm2}}</p>
                    <span>{{currentTime()}}</span>
                </div>
            </div>
            <form class="input">
                <input type="text" placeholder="Написать сообщение..." v-model="command" @input="checker">
                <!-- <input type="text" placeholder="Написать сообщение..." v-model="command" @focus="button = false" @blur="button = true"> -->
                <button @click.prevent="sendText"><img src="@/assets/img/send.svg" alt="" v-if="button == false"></button>               
                <button @click.prevent="showModal = true"><img src="@/assets/img/photo.svg" alt="" v-if="button == true"></button>               
            </form>
        </div>
        <div class="chat1">
            <div class="profile">
                <div class="prof-info">
                    <img src="@/assets/img/Eugene.svg" alt="">
                    <div class="prof-text">
                        <h2>Евгений</h2>
                        <p>Онлайн</p>
                    </div>
                </div>
            </div>
            <div class="text-area">
                <div class="send" v-for="(message2, i) in text2" :key="i" :style="{order: message2.id}" >
                    <p>
                    {{message2.text2}}
                    </p>
                    <span>{{currentTime()}}</span>
                </div>
                <div class="recieve" v-for="(message, i) in text" :key="i" :style="{order: message.id}">
                    <p>
                    {{message.text}}
                    </p>
                    <span>{{currentTime()}}</span>
                </div>
                <div class="pic" v-for="(img, i) in linkImg" :key="i" :style="{order: img.id}">
                    <img :src="img.url" alt="">
                    <p v-if="img.comm.length != 0">{{img.comm}}
                    </p>
                    <span>{{currentTime()}}</span>
                </div>
                <div class="img" v-for="(img2, i) in linkImg2" :key="i" :style="{order: img2.id}">
                    <img :src="img2.url2" alt="">
                    <p v-if="img2.comm2.length != 0">{{img2.comm2}}
                    </p>
                    <span>{{currentTime()}}</span>
                </div>
                <!-- ВЕРНУТЬ НА МЕСТО!!! -->


                <!-- <div class="img" v-for="(img, i) in linkImg" :key="i" :style="{order: img.id}">
                    <img :src="url({imlinkk})" alt="">
                </div>
                <div class="pic" v-for="(pic, i) in lincPic" :key="i" :style="{order: pic.id}">
                    <p>
                        <img :src="imlinkk" alt="">
                    </p>
                </div> -->






                <!-- <div class="img" v-for="(img, idx) in text" :key="idx" :style="{order: img.id}">
                    <img :src="{url}" alt="">
                </div>
                <div class="pic" v-for="(pic, idx) in text" :key="idx" :style="{order: pic.id}">
                    <img :src="{url}" alt="">
                </div> -->
            </div>
            <form class="input">
                <input type="text" placeholder="Написать сообщение..." v-model="command2" @input="checker2">
                <button @click.prevent="sendText2"><img src="@/assets/img/send.svg" alt="" v-if="button2 == false"></button>               
                <button @click.prevent="showModal2 = true"><img src="@/assets/img/photo.svg" alt="" v-if="button2 == true"></button>               
            </form>
        </div>
    </div>
    <Modal
        v-show="showModal" 
        :showModal="showModal"
        @closeModal="showModal = false" 
        @addImg="addImg"   
    />
    <Modal-2
        v-show="showModal2" 
        :showModal2="showModal2"
        @closeModal="showModal2 = false"
        @addImg2="addImg2"
    />
</template>

<script>
import Modal from './Modal.vue'
import Modal2 from './Modal2.vue'
        let element = document.querySelector('.text-area')
        const height = scroll.offsetHeight 
        let order = 0
        let id = 0
    export default {
        components: {Modal, Modal2},
        data(){
            return{
                linkImg: [

                ],
                linkImg2: [

                ],
                text: [
                    
                ],
                text2: [

                ],
                command: '',
                command2: '',
                button: true,
                button2: true,
                clear: '',
                height: '',
                width:'',
                currentId: 0,
                showModal: false,
                showModal2: false,
                imlinkk: 'https://banner2.cleanpng.com/20180403/vre/kisspng-apple-logo-computer-icons-apple-logo-5ac3c99020f360.779171851522780560135.jpg',
            }
        },
        // props: [
        //     'url'
        // ],
        methods: {
            addImg(obj){
                const info = {...obj}
                info.id = this.currentId++
                // info.date = new Date().toLocaleString()
                this.linkImg.push(info)
                console.log(this.currentId);
            },
            addImg2(objj){
                const info2 = {...objj}
                info2.id = this.currentId++
                // info2.date = new Date().toLocaleString()                
                this.linkImg2.push(info2)
                console.log(this.currentId);
            },
            sendText(){
                this.text.push({
                    id:  id, text: this.command, order: order++, id: this.currentId
                    // id:  id, text: this.command, order: order++, date: new Date().toLocaleString() 
                }),
                id = this.currentId++
                console.log(this.currentId);
                // window. scrollTo(0,this.height)
                this.command = this.clear
                if (this.command.length != 0) {
                    this.button = false
                } else {
                    this.button = true
                }
            },
            sendText2(){
                this.text2.push({
                    id: id, text2: this.command2, order: order++, id: this.currentId
                    // id: id, text2: this.command2, order: order++, date: new Date().toLocaleString()
                }),
                id = this.currentId++
                console.log(this.currentId);
                this.command2 = this.clear
                if (this.command2.length != 0) {
                    this.button2 = false
                } else {
                    this.button2 = true
                }
            },
            getText(){
                let localText = localStorage.getItem('list')
                if (localText) {
                    this.text = JSON.parse(localText)
                }
            },
            getText2(){
                let localText2 = localStorage.getItem('list2')
                if (localText2) {
                    this.text2 = JSON.parse(localText2)
                }
            },
            getImg(){
                const localLinks = localStorage.linkImg
                if (localLinks) {
                    this.linkImg = JSON.parse(localLinks)
                }
            },
            getImg2(){
                const localLinks2 = localStorage.linkImg2
                if (localLinks2) {
                    this.linkImg2 = JSON.parse(localLinks2)
                }
            },
            checker(){
                if (this.command.length != 0) {
                    this.button = false
                } else {
                    this.button = true
                }
            },
            checker2(){
                if (this.command2.length != 0) {
                    this.button2 = false
                } else {
                    this.button2 = true
                }
            },
            currentTime() {
                const current = new Date()
                const date = `${current.getHours()}:${current.getMinutes()}`;
                return date;
            }
            // createImg(){
            //     this.linkImg.push({
            //         id: ++id, this.linkImg: this.img, order: order++
            //     }),
            // }
        },
        created(){
            this.getText()
            this.getText2()
            this.getImg()
            this.getImg2()
            // this.getImg()
        },
        watch: {
            // text:{
            //     handler(updatedText){
            //         localStorage.setItem('list', JSON.stringify(this.users))
            //     },
            //     deep: true
            // }
            text:{
                handler(updatedText){
                    localStorage.setItem('list', JSON.stringify(this.text))
                },
                deep: true
            },
            text2:{
                handler(updatedText){
                    localStorage.setItem('list2', JSON.stringify(this.text2))
                },
                deep: true
            },
            link: {
                handler(newLinks) {
                    localStorage.linkImg = JSON.stringify(newLinks)
                    // localStorage.linkImg = JSON.stringify(newLinks)
                    localStorage.linkId = JSON.stringify(this.currentId)
                    console.log(this.linkImg);
                },
                deep: true
            },
            link2: {
                handler(newLinks2) {
                    localStorage.linkImg2 = JSON.stringify(newLinks2)
                    // localStorage.linkImg = JSON.stringify(newLinks)
                    localStorage.linkId = JSON.stringify(this.currentId)
                    console.log(this.linkImg);
                },
                deep: true
            }
        },
        // mounted() {
        //     this.$nextTick(() => {
        //     let element = document.querySelector('.text-area')
        //     const width = element.offsetWidth
        //     const height = element.offsetHeight
        //     this.height = height
        //     this.width = width
        //     })
        // }
    }
</script>

<style lang="scss" scoped>

</style>