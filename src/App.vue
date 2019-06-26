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
                    <option v-for="(product, key) in products['cups']" :key="key" v-bind:value="key" v-if="Object.keys(product['models']).length==1">{{key}}</option>
                </select> 
                <label>Otras marcas disponibles</label>
            </div>
        </div>
        <div class="row">
            <!-- {{ Object.keys(products["cups"]["meluna"]["models"]).length }} -->
        </div>
        <div class="row">
            <div id="left" class="col m6">
                <div class="row" id="title-mobile">
                    <h1>MELUNA CLASSIC</h1>
                </div>
                <div class="row" id="main-slider">
                    <div class="siema">
                        <img src="@/assets/img/meluna/classic/1.jpg">
                        <img src="@/assets/img/meluna/classic/2.jpg">
                        <img src="@/assets/img/meluna/classic/3.jpg">
                        <img src="@/assets/img/meluna/classic/4.jpg">
                        <img src="@/assets/img/meluna/classic/white.jpg">
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
                <div class="row" id="price-origin">
                    <h3>$72.000</h3>
                    <h4>Alemania</h4>
                </div>
                <div class="row">
                    <p id="description">
                        <b>Material</b>: TPE de grado médico hipoalergénico.
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
                    <img src="@/assets/img/certificates.jpg" alt="">
                </div>
            </div>
            <div class="col m6">
                <div class="row" id="title">
                    <h1>MELUNA CLASSIC</h1>
                </div>
                <div class="row">
                    <h3>$72.000</h3>
                    <h4>Alemania</h4>
                </div>
                <div class="row" id="sizes">
                    <div class="col s6 m6 l6 xl6">
                        <div class="row">
                            <div class="col m4 s2">
                                <div id="size">
                                    <p>S</p>
                                </div>
                            </div>
                            <div class="col m8 s10">
                                <div class="large">
                                    <p><b>45mm</b> Diámetro</p>
                                    <p><b>38mm</b> Longitud</p>
                                    <p><b>23ml</b> Capacidad</p>
                                    <p><b>10mm</b> Terminación</p>
                                </div>
                                <div class="small">
                                    <p><b>45mm</b> x <b>38mm</b> x <b>23mm</b></p>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="col s6 m6 l6 xl6">
                        <div class="row">
                            <div class="col m4 s2">
                                <div id="size">
                                    <p>M</p>
                                </div>
                            </div>
                            <div class="col m8 s10">
                                <div class="large">
                                    <p><b>45mm</b> Diámetro</p>
                                    <p><b>38mm</b> Longitud</p>
                                    <p><b>23ml</b> Capacidad</p>
                                    <p><b>10mm</b> Terminación</p>
                                </div>
                                <div class="small">
                                    <p><b>45mm</b> x <b>38mm</b> x <b>23mm</b></p>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="col s6 m6 l6 xl6">
                        <div class="row">
                            <div class="col m4 s2">
                                <div id="size">
                                    <p>L</p>
                                </div>
                            </div>
                            <div class="col m8 s10">
                                <div class="large">
                                    <p><b>45mm</b> Diámetro</p>
                                    <p><b>38mm</b> Longitud</p>
                                    <p><b>23ml</b> Capacidad</p>
                                    <p><b>10mm</b> Terminación</p>
                                </div>
                                <div class="small">
                                    <p><b>45mm</b> x <b>38mm</b> x <b>23mm</b></p>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="col s6 m6 l6 xl6">
                        <div class="row">
                            <div class="col m4 s2">
                                <div id="size">
                                    <p class="xl">XL</p>
                                </div>
                            </div>
                            <div class="col m8 s10">
                                <div class="large">
                                    <p><b>45mm</b> Diámetro</p>
                                    <p><b>38mm</b> Longitud</p>
                                    <p><b>23ml</b> Capacidad</p>
                                    <p><b>10mm</b> Terminación</p>
                                </div>
                                <div class="small">
                                    <p><b>45mm</b> x <b>38mm</b> x <b>23mm</b></p>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="col s6 m6 l6 xl6">
                        <div class="row">
                            <div class="col m4 s2">
                                <div id="size">
                                    <p>S</p>
                                    <span>Shorty</span>
                                </div>
                            </div>
                            <div class="col m8 s10">
                                <div class="large">
                                    <p><b>45mm</b> Diámetro</p>
                                    <p><b>38mm</b> Longitud</p>
                                    <p><b>23ml</b> Capacidad</p>
                                    <p><b>10mm</b> Terminación</p>
                                </div>
                                <div class="small">
                                    <p><b>45mm</b> x <b>38mm</b> x <b>23mm</b></p>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="col s6 m6 l6 xl6">
                        <div class="row">
                            <div class="col m4 s2">
                                <div id="size">
                                    <p>M</p> 
                                    <span>Shorty</span>
                                </div>
                            </div>
                            <div class="col m8 s10">
                                <div class="large">
                                    <p><b>45mm</b> Diámetro</p>
                                    <p><b>38mm</b> Longitud</p>
                                    <p><b>23ml</b> Capacidad</p>
                                    <p><b>10mm</b> Terminación</p>
                                </div>
                                <div class="small">
                                    <p><b>45mm</b> x <b>38mm</b> x <b>23mm</b></p>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="col s6 m6 l6 xl6">
                        <div class="row">
                            <div class="col m4 s2">
                                <div id="size">
                                    <p>L</p>
                                    <span>Shorty</span>
                                </div>
                            </div>
                            <div class="col m8 s10">
                                <div class="large">
                                    <p><b>45mm</b> Diámetro</p>
                                    <p><b>38mm</b> Longitud</p>
                                    <p><b>23ml</b> Capacidad</p>
                                    <p><b>10mm</b> Terminación</p>
                                </div>
                                <div class="small">
                                    <p><b>45mm</b> x <b>38mm</b> x <b>23mm</b></p>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="col s6 m6 l6 xl6">
                        <div class="row">
                            <div class="col m4 s2">
                                <div id="size">
                                    <p class="xl">XL</p> 
                                    <span>Shorty</span>
                                </div>
                            </div>
                            <div class="col m8 s10">
                                <div class="large">
                                    <p><b>45mm</b> Diámetro</p>
                                    <p><b>38mm</b> Longitud</p>
                                    <p><b>23ml</b> Capacidad</p>
                                    <p><b>10mm</b> Terminación</p>
                                </div>
                                <div class="small">
                                    <p><b>45mm</b> x <b>38mm</b> x <b>23mm</b></p>
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
import products from '@/assets/products.json';

import 'materialize-css'
import 'materialize-css/dist/css/materialize.css';
import Siema from 'siema'

export default {
  name: 'app',
  components: {
  },
  data: function () {
    return {
      selected: this.selected,
      products: products
    }
  },
  methods: {
    goToOption: function() {
      history.pushState(null, '', `/${this.selected}`);   
    }
  },
  mounted() {
    this.selected = location.pathname.substring(1)?location.pathname.substring(1):'meluna/classic'
    this.mySiema = new Siema({selector: '.siema'})
    document.querySelector('#prev').addEventListener('click', () => this.mySiema.prev());
    document.querySelector('#next').addEventListener('click', () => this.mySiema.next());
    console.log(products)
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
