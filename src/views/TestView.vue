<!--<template>
    <div class="test">
        <h1>{{ title }}</h1>
        <div class="fig">
            <figure v-for="(v,k) in data" :key="k"  @click="result(v)">
                <img :src="v.name">
                <p>이미지{{ v.id }}</p>
            </figure>
            <div class="toggle" :class="{active:isActive}" @click="modal">
                <img :src="name">
                <p>이미지{{ id }}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            title: 'photo list',
            isActive: true,
            data : [
                {id:1, name:'../img/01.jpg'},
                {id:2, name:'../img/02.jpg'},
                {id:3, name:'../img/03.jpg'},
                {id:4, name:'../img/04.jpg'},
                {id:5, name:'../img/05.jpg'},
                {id:6, name:'../img/06.jpg'},
                {id:7, name:'../img/07.jpg'},
                {id:8, name:'../img/08.jpg'},
                {id:9, name:'../img/09.jpg'},
                {id:10, name:'../img/10.jpg'}
            ]
        }
    },
    methods: {
        result(v){
            // console.log(e.currentTarget.src.substr(22));
            this.isActive = !this.isActive;
            // document.querySelector('')
            // imgUrl =`../${e.currentTarget.src.substr(22)}`
            console.log(this)
            this.name =v.name;
        },
        modal(){
            this.isActive = !this.isActive;
        }
    }
}
</script>
<style lang="scss">
    .fig{
        display: flex;
        flex-wrap: wrap;
        figure{
            position: relative;
            img{
                width: 250px;
            }
        }
        .toggle{
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%,-50%);
            background: rgba(56, 56, 56,0.5);
            width: 100%;
            height: 100vh;
            &.active{
                display: none;
            }
        }
    }
</style>

-----------------------------여기까지 내가 한거...
-->
<template>
    <div class="test">
      <h1>Photo List</h1>
      <ul class="list">
        <ItemList />
        <!-- <li v-for="v in data" :key="v.id" @click="()=>open(v.id)">
            <img :src="v.src">
            <p>{{v.name}}</p>
        </li> -->
      </ul>

      <div 
      class="pop" 
      :class="{active:isActive}" 
      v-html="detail" 
      @click="close"></div>

    </div>
</template>

<script>
import ItemList from '../components/Items.vue';

export default {
    components:{
        ItemList
    },
    data(){
        return{
            data : [
                {id:0, name:'이미지1' ,src:"./img/01.jpg"},
                {id:1, name:'이미지2' ,src:"./img/02.jpg"},
                {id:2, name:'이미지3' ,src:"./img/03.jpg"},
                {id:3, name:'이미지4' ,src:"./img/04.jpg"},
                {id:4, name:'이미지5' ,src:"./img/05.jpg"},
                {id:5, name:'이미지5' ,src:"./img/06.jpg"},
                {id:6, name:'이미지5' ,src:"./img/07.jpg"},
                {id:7, name:'이미지5' ,src:"./img/08.jpg"},
                {id:8, name:'이미지5' ,src:"./img/09.jpg"},
                {id:9, name:'이미지5' ,src:"./img/10.jpg"},
            ],
            detail:'',
            isActive:false
        }        
    },
    methods:{
        open(id){
            this.isActive = true;
            this.detail = `<img src=${this.data[id].src}>`;            
        },
        close(e){
            if(e.target.nodeName != 'IMG')
            this.isActive = false;
        }
    }
}
</script>
<style lang="scss">
ul{list-style-type: none; margin:0; padding:0;}
    .list{
        width:80%; margin:0 auto;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        li{
            width:30%; margin-bottom:5%;
            img{width:100%;}
        }
    }
    .pop{
        width:100%; height:100%;
        position:fixed; left:0; top:0; 
        display: flex;
        justify-content: center;
        align-items: center;
        background: rgba(0,0,0,0.6);
        display: none;
        &.active{display:flex;}
    }
</style>