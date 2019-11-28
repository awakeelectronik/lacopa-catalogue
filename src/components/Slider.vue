<template>
    <div class="row" id="main-slider">

{{ loaded }}
        <div class="siema">
            <img v-for="(image, key) in loaded.images" :key="key" :src="getImage(image)" :alt="`${loaded.brand} ${loaded.model} ${image} cup`">
            <iframe style="width:100%" height="450" :src="`https://www.youtube.com/embed/${loaded.video}`" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        </div>
        <svg id="prev" width="50" height="50" viewBox="0 0 18 18" xmlns="http://www.w3.org/2000/svg">
            <g fill="#26a69a" fill-rule="evenodd">
                <path d="M6.646 5.354l4 4 .354.353.707-.707-.353-.354-4-4L7 4.293 6.293 5z"></path>
                <path d="M7.354 13.354l4-4L11.707 9 11 8.293l-.354.353-4 4-.353.354.707.707z"></path>
            </g>
        </svg>
        <svg id="next" width="50" height="50" viewBox="0 0 18 18" xmlns="http://www.w3.org/2000/svg">
            <g fill="#26a69a" fill-rule="evenodd">
                <path d="M6.646 5.354l4 4 .354.353.707-.707-.353-.354-4-4L7 4.293 6.293 5z"></path>
                <path d="M7.354 13.354l4-4L11.707 9 11 8.293l-.354.353-4 4-.353.354.707.707z"></path>
            </g>
        </svg>
    </div>
</template>

<script>
import Siema from 'siema'

export default {
  name: 'Slider',
  props: [
      'loaded'
  ],
  methods: {
    reloadSiema: function() {
        document.querySelector(".siema").style.height = null
        var height = document.querySelector(".siema").offsetHeight
        document.querySelector('#prev').removeEventListener('click', () => this.mySiema.prev(), false);
        document.querySelector('#next').removeEventListener('click', () => this.mySiema.prev(), false);
        this.mySiema.destroy(true)  
        document.querySelector(".siema").setAttribute("style", "height: "+ height + "px")
        console.log('height' + height);
        
        setTimeout(function() { 
            console.log('timeout');
            this.mySiema = new Siema({
                selector: '.siema',
                loop: true,
                easing: 'cubic-bezier(.17,.67,.22,1.34)'
            })
            document.querySelector('#prev').addEventListener('click', () => this.mySiema.prev());
            document.querySelector('#next').addEventListener('click', () => this.mySiema.next());

            document.querySelector(".siema").style.height = null
        }, 1100);
    },
    getImage(name) {
        let image = require(`@/assets/img/${this.loaded.brand}/${this.loaded.model}/${name}.jpg`)
        if(this.loaded.images[this.loaded.images.length-1]==name&&this.mySiema){
            this.reloadSiema()
            console.log('imprimio el reload');
        }
        return image
    }
  },
    mounted() {
        console.log('mounted');
        this.mySiema = new Siema({
            selector: '.siema',
            loop: true
        })
        document.querySelector('#prev').addEventListener('click', () => this.mySiema.prev());
        document.querySelector('#next').addEventListener('click', () => this.mySiema.next());
    }

}
</script>