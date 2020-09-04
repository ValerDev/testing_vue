<template>
  <div id="product-wrapper">
    <div class="details">
      <h2>Cap Toe Sneaker</h2>
      <div class="header-part">
        <div class="add-season__block" @click.prevent="secondStep = !secondStep">
          <div v-if='!secondStep'>
            <template>
              <el-button
                  class="season-select"
                  placeholder="Add Season">
                  + Add Season
              </el-button>
            </template>
          </div>
          <div v-else-if="secondStep" >
            <div class="added-season__inner">
              <div class="added-season__el">AW21</div>
              <div class="added-season__el">SS21</div>
              <div class="added-season__el">AW21</div>
              <div class="added-season__el">+3</div>
            </div>
          </div>
        </div>
        <div class="add-label__block">
          <div v-if='!isAddedLabel'>
            <el-button class="label-select" @click="isAddedLabel = !isAddedLabel">
              + Add Label
            </el-button>
          </div>
          <div v-else-if="!sAddedLabel" >
            <div class="added-label__inner">
              <div class="added-label__el">Core</div>
              <div class="added-label__el">Waterproof</div>
              <div class="added-label__el">Vegan</div>
              <div class="added-label__el">+2</div>
            </div>
          </div>
        </div>
      </div>
      <div class="types">
        <div class="colors">
          <div class="process">
          <h5>Colors</h5>
            <template>
              <div v-if="!pickColor" class="color-pick">
                <el-button type="primary" class="detail-button" @click="pickColor = !pickColor">
                  <img src="../assets/img/icons/edit-filled.svg" alt=""  class=""/>
                  <span>Add</span>
                </el-button>
              </div>
              <div v-else-if="pickColor && !showPickedColorsBlock" class="block detail__color">
                <div class="color-pick__row">
                  <div
                    v-for="(color, i) in colors"
                    :key="i" class="color-pick__el"
                    :style="'background-color:' + color.color"
                    :background='color.color'
                    :name='color.name'
                    ref="addColor"
                    @click="addColor"
                  >
                    <div class="color-pick__hover"><i class="el-icon-circle-plus"></i></div>
                  </div>
                </div>
                <div class="color-pick__row" >
                  <h4>Selected Colors</h4>
                  <div class="color-pick__inner">
                    <div
                      v-for='(pickedColor, i) in pickedColors'
                      :key='i'
                      class="picked-color__row"
                    >
                      <div class="picked-color__el" :style="'background-color:' + pickedColor.color" ></div>
                      <div class="picked-color_del" @click="pickedColors.splice(i,1)"><i class="el-icon-delete"></i></div>
                    </div>
                  </div>
                  <div class="pick-control">
                    <el-button class="cancel-pick" icon='el-icon-circle-close' @click='pickColor = false'>Cancel</el-button>
                    <el-button class="save-pick" icon='el-icon-s-order'  @click='showPickedColors'>Save</el-button>
                  </div>
                </div>
              </div>
              <div v-if='showPickedColorsBlock' class="picked-colors__inner">
                <div v-for="(color,i) in pickedColors" :key="i" class="pickedColor" :style="color.name ==='White' ? 'color:grey; background-color:white' : 'background-color:' + color.color">
                  <span>{{color.name}}</span>
                </div>
              </div>
            </template>
          </div>
        </div>
      </div>
            <div class="shopping details">
        <div class="shopping__row first--shopping__row">
          <div class="little-icon ">
            <img src="../assets/img/icons/supplier-large.svg" />
          </div>
          <el-button v-if="isAddedSupplier" type="primary" class="detail-button" @click="isAddedSupplier = !isAddedSupplier">
            <img src="../assets/img/icons/plus.svg" alt=""  class=""/>
            <span>Add Supplier</span>
          </el-button>
          <div v-else class="flags">
            <div class="flags-first-block flag-block">
              <img src="../assets/img/flags/prt.svg" alt="">
              <span>Albano Perreira</span>
            </div>
            <div class="flags-secound-block flag-block">
              <img src="../assets/img/flags/ita.svg" alt="">
              <span>Shoelutiouns</span>
            </div>
            <div class="flags-more-block">
              <span>+2 MORE</span>
            </div>
          </div>
        </div>
         <div v-if="isAddPricing" class="shopping__row secound--shopping__row" @click="isAddPricing = !isAddPricing">
          <div class="little-icon ">
            <img src="../assets/img/icons/retail-price-large.svg" />
          </div>
          <el-button type="primary" class="detail-button">
            <img src="../assets/img/icons/plus.svg" alt=""  class=""/>
            <span>Add Pricing</span>
          </el-button>
        </div>
        <div v-else class="contentAddPricing">
              <div class="addPricingBlock addPricingBlock-first">
                <img class="switch" src="../assets/img/icons/switch.svg" alt="">
                <img src="../assets/img/icons/factory-price-large.svg" alt="">
                <span class="price">&euro;35</span>
                <span class="info">FACTORY PRICE</span>

              </div>
              <div class="mathSign">x</div>
              <div class="addPricingBlock addPricingBlock-secound">
                <img src="../assets/img/icons/markup-large.svg" alt="">
                <span class="price">5.5</span>
                <span class="info">MARKUP</span>

              </div>
              <div class="mathSign">=</div>
              <div class="addPricingBlock addPricingBlock-third">
                <img src="../assets/img/icons/retail-price-large.svg" alt="">
                <span class="price">&euro;185</span>
                <span class="info">RETAIL PRICE</span>

              </div>
        </div>
      </div>
    </div>
    <div id="background">
      <backgrounImg />
    </div>
  </div>
</template>

<script>
import backgrounImg from './background'
export default {
  components: {
    backgrounImg
  },
  data () {
    return {
      secondStep: false,
      isAddedLabel: false,
      pickColor: false,
      showColor: true,
      showPickedColorsBlock: false,
      isAddPricing: true,
      isAddedSupplier: true,
      colors: [
        {
          name: 'White',
          color: '#ffffff'
        },
        {
          name: 'Light Grey',
          color: '#9e9c9c'
        },
        {
          name: 'Grey',
          color: '#696969'
        },
        {
          name: 'Dark Grey',
          color: '#474747'
        },
        {
          name: 'Black',
          color: '#000000'
        },
        {
          name: 'Scarlet',
          color: '#e43434'
        },
        {
          name: 'Maroon',
          color: '#690707'
        },
        {
          name: 'Smooth Yellow',
          color: '#d1cb73'
        },
        {
          name: 'Yellow',
          color: '#dab220'
        },
        {
          name: 'Dark Yellow',
          color: '#817505'
        },
        {
          name: 'Light Green',
          color: '#20d83d'
        },
        {
          name: 'Dark Green',
          color: '#165820'
        },
        {
          name: 'Green',
          color: '#0da53f'
        },
        {
          name: 'Light Skyblue',
          color: '#30c8f7'
        },
        {
          name: 'Dark Skyblue',
          color: '#0e3c4e'
        },
        {
          name: 'Dark Blue',
          color: '#1a2268'
        },
        {
          name: 'Blue',
          color: '#063156'
        },
        {
          name: 'Violet',
          color: '#c463d0'
        },
        {
          name: 'Purple',
          color: '#ca1bbc'
        },
        {
          name: 'Dark Purple',
          color: '#550741'
        },
        {
          name: 'Light Orange',
          color: '#be8228'
        },
        {
          name: 'Dark Orange',
          color: '#68430b'
        },
        {
          name: 'Neon Green',
          color: '#07f170'
        },
        {
          name: 'Neon Dark Green',
          color: '#2a5f42'
        },
        {
          name: ' Dark Green',
          color: '#0f3f25'
        }
      ],
      pickedColors: [
        {
          name: ' Dark Green',
          color: '#0f3f25'
        },
        {
          name: 'Light Orange',
          color: '#be8228'
        },
        {
          name: 'Violet',
          color: '#c463d0'
        }
      ]
    }
  },
  methods: {
    addColor () {
      const pickTheColor = this.$refs.addColor
      pickTheColor.forEach(el => {
        el.onclick = (e) => {
          this.pickedColors.push({
            name: el.attributes.name.value,
            color: el.attributes.background.value
          })
          console.log(this.$refs.addColor)
        }
      })
    },
    showPickedColors () {
      this.showPickedColorsBlock = true
      this.pickColor = true
    }
  }
}
</script>

<style lang='sass'>
@import '../assets/sass/mainProduct/mainProduct'
</style>
