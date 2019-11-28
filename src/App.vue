<template>
  <div id="app">
    <div class="section" id="navbar">
        <div class="row">
            <div id="menu" class="col m3 l2 offset-m9">
                <ul>
                    <li>
                        <a href="#"><u>Blog</u></a>
                    </li>
                    <li>
                        <a href="#"><u>Contacto</u></a>
                    </li>

                </ul>
            </div>
        </div>
    </div>
    <div class="container">
        <div class="row">
            <div class="input-field col s12 m12 l12 xl12">
                <select v-model="selected" v-on:change="goToOption">
                    <optgroup v-for="(product, key) in products['cups']" :key="key" v-bind:label="key" v-if="Object.keys(product['models']).length>1">
                        <option v-for="(model, k) in product['models']" :key="k" v-bind:value="key+'/'+k">{{k}}</option>
                    </optgroup>
                    <option v-for="(product, key) in products['cups']" :key="key" v-bind:value="key+'/'+Object.keys(product['models'])[0]" v-if="Object.keys(product['models']).length==1">{{key}}</option>
                </select> 
                <label>Otras marcas disponibles</label>
            </div>
        </div>
        <div class="row">
            {{ loaded }}
        </div>
        <div class="row" v-if="loaded">
            <div id="left" class="col m6">
                <div class="row" id="title-mobile">
                    <h1>{{ `${loaded.brand} ${loaded.model}` }}</h1>
                </div>
                <Slider :loaded="loaded"></Slider>
                <div class="row" id="price-origin">
                    <h3>{{ loaded.price }}</h3>
                    <h4>{{ loaded.origin }}</h4>
                </div>
                <div class="row">
                    <p id="description">
                        <b>{{ loaded.material }}</b>: {{ loaded.material }}.
                    </p>
                </div>
                <div class="row">
                    <div class="col m4 s4">
                        <h4>SOFT (suave)</h4>
                        <img src="@/assets/img/meLuna-morada.jpg" alt="">
                        <p>Plateado escarchado, rosa y azul aguamarina.</p>
                    </div>
                    <div class="col m4 s4">
                        <h4>SOFT (suave)</h4>
                        <img src="@/assets/img/meLuna-morada.jpg" alt="">
                        <p>Plateado escarchado, rosa y azul aguamarina.</p>
                    </div>
                    <div class="col m4 s4">
                        <h4>SOFT (suave)</h4>
                        <img src="@/assets/img/meLuna-morada.jpg" alt="">
                        <p>Plateado escarchado, rosa y azul aguamarina.</p>
                    </div>
                </div>
                <div class="row">
                    <img :src='`@/assets/img/certificates.jpg`' alt="">
                </div>
            </div>
            <div class="col m6">
                <div class="row" id="title">
                    <h1>{{ `${loaded.brand} ${loaded.model}` }}</h1>
                </div>
                <div class="row">
                    <h3>{{ loaded.price }}</h3>
                    <h4>{{ loaded.origin }}</h4>
                </div>
                <div class="row" id="sizes">
                    <div class="col s6 m6 l6 xl6" v-for="size in loaded.sizes">
                        <div class="row">
                            <div class="col m4 s2">
                                <div id="size">
                                    <p>{{ size.letter }}</p>
                                </div>
                            </div>
                            <div class="col m8 s10">
                                <div class="large">
                                    <p><b>{{ size.diameter }}mm </b>Diámetro</p>
                                    <p><b>{{ size.length }}mm </b>Longitud</p>
                                    <p><b>{{ size.capacity }}ml</b> Capacidad</p>
                                    <p><b>{{ size.stem }}mm </b>Terminación</p>
                                </div>
                                <div class="small">
                                    <p><b>{{ size.diameter }}mm</b> x <b>{{ size.length }}mm</b> x <b>{{ size.capacity }}ml</b></p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
  </div>
</template>
<script>

/* eslint-disable */ 
import products from '@/assets/products.json'

import 'materialize-css'
import 'materialize-css/dist/css/materialize.css'
import Slider from './components/Slider'

export default {
  name: 'app',
  components: {
      Slider
  },
  data: function () {
    return {
      selected: this.selected,
      products: products,
      loaded: this.loaded
    }
  },
  methods: {
    goToOption: function() {
        history.pushState(null, '', `/${this.selected}`)
        this.loadSelected()
    },
    loadSelected: function() {
        const [brand, model] = this.selected.split('/')
        this.loaded = {
            "brand": brand,
            "model": model,
            "material": products["cups"][brand].material,
            "origin": products["cups"][brand].origin,
            "certified": products["cups"][brand].certified,
        }
        Object.assign(this.loaded, products["cups"][brand]["models"][model])
    }
  },
  created() {
    this.selected = location.pathname.substring(1)?location.pathname.substring(1):'meluna/classic'
    this.loadSelected()
  },
  update(){
  },
  beforeDestroy() {
  }
}

document.addEventListener('DOMContentLoaded', function() {
    var elems = document.querySelectorAll('select');
    var instances = M.FormSelect.init(elems, {});
});
</script>
 
<style lang="scss">
    @import 'assets/style';
</style>
